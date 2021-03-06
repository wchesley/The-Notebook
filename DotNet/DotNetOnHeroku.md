# Dotnet On Heroku: 
[Heroku](www.heroku.com) offers no native support (as of yet) for .NET applications. This is my process for how I deployed [WishList](https://wishlist-bytes.herokuapp.com/) to Heroku. Thankfully the set up is not all that complex and there are tons of third party buildpacks that allow .NET to run on Heroku.

## Initial Setup: 
- Create your app on Heroku, as you would with any other app. You do not have to have a code base for this yet.   
- Once your app is provisioned; GoTo the heroku settings page for your new app. There you will see buildpacks just underneath Config Vars
    - Click Add Buildpack and point it to: `https://github.com/jincod/dotnetcore-buildpack`  
- This is all you need for a basic .NET setup, you can now deploy your code to this dyno via the Heroku CLI or web interface. 

---
## Caveats: 
## Entity Framework Core Migrations

You cannot run migrations with the `dotnet ef` commands using **.NET Local Tools** once the app is built. Alternatives include:

### Enabling Automatic Migrations

- Ensure the `ASPNETCORE_ENVIRONMENT` environment variable is set to `Production`. ASP.NET Core scaffolding tools may create files that explicitly set it to `Development`. Heroku config will override this (`heroku config:set ASPNETCORE_ENVIRONMENT=Production`).
- Configure your app to automatically run migrations at startup by adding the following to the `.csproj` file:

```xml
<Target Name="PrePublishTarget" AfterTargets="Publish">
  <Exec Command="dotnet ef database update" />
</Target>
```

- Configure your connection string string appropriately, for example, for PostgreSQL:

`sslmode=Prefer;Trust Server Certificate=true`

### Manually Running Migration Scripts on the Database

- Manually run SQL scripts generated by Entity Framework Core in your app's database. For example, use PG Admin to connect your Heroku Postgres service.
---

## .NET with Selenium on Heroku: 
Selenium on heroku is no straight forward task. There are two additional buildpacks, both offered by Heroku that we'll need to be added to the dyno for it to work. The first buildpack downloads and installs Google Chrome to they Dyno, the second grabs the chromedriver.    
1. [https://github.com/heroku/heroku-buildpack-google-chrome](https://github.com/heroku/heroku-buildpack-google-chrome)
2. [https://github.com/heroku/heroku-buildpack-chromedriver](https://github.com/heroku/heroku-buildpack-chromedriver)



### Google Chrome Command Line Flags

The Google Chrome buildpack installs shims that always add `--headless`, `--disable-gpu`, 
`--no-sandbox`, and `--remote-debugging-port=9222` to any `google-chrome` 
command as you'll have trouble running Chrome on a Heroku dyno otherwise.

You'll have two of these shims on your path: `google-chrome` and
`google-chrome-$GOOGLE_CHROME_CHANNEL`. They both point to the binary of
the selected channel.

### Selenium-ChromeDriver

To use Selenium with this buildpack, you'll also need Chrome's webdriver.
This buildpack does not install chromedriver, but there is a
[chromedriver buildpack](https://github.com/heroku/heroku-buildpack-chromedriver)
also available.

Additionally, chromedriver expects Chrome to be installed at `/usr/bin/google-chrome`,
but that's a read-only filesystem in a Heroku slug. You'll need to tell Selenium/chromedriver
that the chrome binary is at `/app/.apt/usr/bin/google-chrome` instead.

To make that easier, this buildpack makes `$GOOGLE_CHROME_BIN`, and
`$GOOGLE_CHROME_SHIM` available as environment variables. With them, you can 
use the standard location locally and the custom location on Heroku.


## Running Selenium: 
By default, my $PATH for Selenium looks as follows: 
`CHROMEDRIVER_PATH`:` /app/.chromedriver/bin/chromedriver`
`GOOGLE_CHROME_BIN`:`/app/.apt/usr/bin/google-chrome`

In the development enviroment (my local enviroment) I would keep chromedriver.exe within the root project directory and call upon it as follows: 
```csharp
 public ChromeDriver createBrowser()
        {
            var options = new ChromeOptions();
            options.AddArguments("whitelisted-ips=''", "headless");
            ChromeDriver browser = new ChromeDriver("./", options);
            //give pages 30 seconds to respond before timeing out: 
            browser.Manage().Timeouts().ImplicitWait = TimeSpan.FromSeconds(30);
            return browser;
        }
```

Selenium likes to append '/chromedriver' to the path that is manually specified. So when launched to Heroku; despite chromedriver.exe being located in the root project directory Selenium would still return `OpenQA.Selenium.DriverServiceNotFoundException: The file ./chromedriver does not exist. The driver can be downloaded at http://chromedriver.storage.googleapis.com/index.html` 

I was not able to manually specify the path to chromedriver without Selenium adding '/chromedriver' every time. On Windows Machines this should work just fine, however for a Linux install the chromedriver is labeled as '.chromedriver' making it hidden by default. Trying to call it with `ChromeDriver browser = new ChromeDriver("./.chromedriver", options);` still shows: The file ./.chromedriver/chromedriver doesn't exist. Thankfully however the fix for this is really simple: we just need to let Selenium use PATH instead of passing it the argument. So instead we write: 
```csharp
 public ChromeDriver createBrowser()
        {
            var options = new ChromeOptions();
            options.AddArguments("whitelisted-ips=''", "headless");
            ChromeDriver browser = new ChromeDriver(options); //This forces Selenium to use System PATH
            //give pages 30 seconds to respond before timeing out: 
            browser.Manage().Timeouts().ImplicitWait = TimeSpan.FromSeconds(30);
            return browser;
        } 
```

Success! Selenium should now be able to run both locally and on Heroku!

## Postgres 
I ran into quite a bit of trouble running postgres on heroku but it can be done, and here's how I did it: 

### Deploying

First issue was getting my Database set up script into Heroku, since I cannot run any `dotnet ef` commands in Heroku. I had to install postgres locally, run my migrations there, then import that database into Heroku. Heroku even has [import/export](https://devcenter.heroku.com/articles/heroku-postgres-import-export#import) information on their site.  
They offer a command to dump the database to make it easier for importing:  
`PGPASSWORD=mypassword pg_dump -Fc --no-acl --no-owner -h localhost -U myuser mydb > mydb.dump`   
But when I went to import the dump within heroku I received an error:  
`pg_restore: [archiver] did not find magic string in file header`  
The 'resolution' offered by Heroku states the dump needs to be made with the `-Fc` command...but mine was...anyway I need a new way to get my migrations onto Heroku, onto Google. After quite a bit of searching I came across [this](https://stackoverflow.com/questions/31057998/migrating-database-from-local-development-to-heroku-django-1-8) StackOverflow post.  It offered a way to directly migrate the existing database to Heroku. The OP warns to only do this if the database is small, in this case. It's empty, just the tables and relations are set up. The command from the original post is this:   
`pg_dump --no-acl --no-owner -h localhost -U myuser myd | heroku pg:psql`  
Heroku complained that it needs an app to point this at so adjust as follows:  
`pg_dump --no-acl --no-owner -h localhost -U myuser myd | heroku pg:psql -a YourAppName`  

### Heroku Connection
Thanks to [this](https://github.com/nbarbettini/little-aspnetcore-book/pull/49/files) pull request, I was able to get Heroku connected properly. The following is a direct exerpt from the pull request: 
 
### Preparing the application for Heroku Postgres

Right now, your application reads the value of the `DefaultConnection` configuration value at runtime to learn how to connect to the PostgreSQL database running on your development machine. On Heroku, the environment will be different. Heroku sets an environment variable called `DATABASE_URL` for your application to read. You must change your code to read this environment variable instead of the configuration if it detects that it is running on Heroku. In order to tell your application that it's running on Heroku, you'll configure it to read a the environment variable `ASPNETCORE_ENVIRONMENT`. This environment variable has been set to the value `Development` for you automatically by Visual Studio Code so far. You can configure your application to run in "Heroku mode" if this environment variable's value is set to `Production`. Change the following code in `Startup.cs`:

```csharp
services.AddEntityFrameworkNpgsql().AddDbContext<ApplicationDbContext>(options =>
    options.UseNpgsql(Configuration.GetConnectionString("DefaultConnection")));
```

to this:

```csharp
services.AddEntityFrameworkNpgsql().AddDbContext<ApplicationDbContext>(options =>
{
    var env = Environment.GetEnvironmentVariable("ASPNETCORE_ENVIRONMENT");
    string connStr;
    // Depending on if in development or production, use either Heroku-provided
    // connection string, or development connection string from env var.
    if (env == "Development")
    {
        // Use connection string from file.
        connStr = Configuration.GetConnectionString("ApplicationDbContext");
    }
    else
    {
        // Use connection string provided at runtime by Heroku.
        var connUrl = Environment.GetEnvironmentVariable("DATABASE_URL");
        // Parse connection URL to connection string for Npgsql
        connUrl = connUrl.Replace("postgres://", string.Empty);
        var pgUserPass = connUrl.Split("@")[0];
        var pgHostPortDb = connUrl.Split("@")[1];
        var pgHostPort = pgHostPortDb.Split("/")[0];
        var pgDb = pgHostPortDb.Split("/")[1];
        var pgUser = pgUserPass.Split(":")[0];
        var pgPass = pgUserPass.Split(":")[1];
        var pgHost = pgHostPort.Split(":")[0];
        var pgPort = pgHostPort.Split(":")[1];
        connStr = $"Server={pgHost};Port={pgPort};User Id={pgUser};Password={pgPass};Database={pgDb}";
    }
    // Whether the connection string came from the local development configuration file
    // or from the environment variable from Heroku, use it to set up your DbContext.
    options.UseNpgsql(connStr);
});
```

It's a lot more code, but it's a powerful change. This will allow your app to decide as it starts up whether it's running on your local development computer or deployed in production mode on Heroku, and connect to the database meant for it properly in both cases.

Don't mind the code related to parsing the "connection URL". Some platforms, such as Ruby on Rails, can use this value as is. Unfortunately, you must do a bit of extra work to convert it into a value compatible with Entity Framework Core. Feel free to refactor this parsing code into a utility class elsewhere in your application later if you want to.

**Before continuing**, you must make sure the `ASPNETCORE_ENVIRONMENT` environment variable is set to `Production` so that your application will correctly connect to the database once it's deployed. You can use Heroku's web portal to do this, but to continue with the CLI theme of the book, use the Heroku CLI to do this instead with the `heroku config:set ASPNETCORE_ENVIRONMENT=Production` command.