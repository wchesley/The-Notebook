# Nextcloud 20.0.3 Setup
Personally I never cared for snap packages, I've heard they can have weird issues in the long term running of packages. I prefer to set things up the manual way. This is how I set up my nextcloud server, and have it configured. 

## Install Nextcloud: 
Use wget to grab the latest release of nextcloud, I had to go to their site to find it's proper address: 
```bash
wget https://download.nextcloud.com/server/releases/nextcloud-20.0.3.zip
```
I used unzip to extract the .zip file into /var/www: 
```bash
sudo apt install unzip

sudo unzip nextcloud-20.0.3.zip -d /var/www
```
That will 'install' nextcloud but it still needs to be configured, next up, the database: 

## Configure Nextcloud database using MariaDB

Provided it's installed already, else install it via
```bash
sudo apt-get install mariadb-server

# Set up server script:
sudo mysql_secure_installation
```
After MariaDB is installed activate it's shell: 
```bash
sudo mysql
```
Then create a database to host nextcloud, name can be whatever you want just remember it for when we go to configure nextcloud: 
```sql
create database nextcloud; 
```
Create a database user for nextcloud to use: 
```sql
create user nextclouduser@localhost identified by 'your-password';
# Where nextclouduser is the username for Nextcloud and 'your-password' is your desired password for this user
```
Grant privileges to this new user on the nextcloud database: 
```sql
grant all privileges on nextcloud.* to nextclouduser@localhost identified by 'your-password';
```
flush MariaDB privileges and exit the shell: 
```sql
flush privileges; 
exit; 
```

## Webserver config (Apache)

We need to create a configuration file for nextcloud in apache: 
```bash
# Use your preferred text editor, mine is nano: 
sudo nano /etc/apache2/sites-available/nextcloud.conf
```

An example config file looks like: 
```xml
<VirtualHost *:80>
        DocumentRoot /var/www/nextcloud
        ServerName nextcloud.example.com

        ErrorLog ${APACHE_LOG_DIR}/nextcloud.error
        CustomLog ${APACHE_LOG_DIR}/nextcloud.access combined

        <Directory /var/www/nextcloud/>
            Require all granted
            Options FollowSymlinks MultiViews
            AllowOverride All

           <IfModule mod_dav.c>
               Dav off
           </IfModule>

        SetEnv HOME /var/www/nextcloud
        SetEnv HTTP_HOME /var/www/nextcloud
        Satisfy Any

       </Directory>

</VirtualHost>
```
Save the file and exit the text editor

Enable the new virtual host: 
```bash 
sudo a2ensite nextcloud.conf
```
Enable the apache modules if they are not already: 
```bash
sudo a2enmod rewrite headers env dir mime setenvif ssl
```

Test for syntax errors in the conf files: 
```bash
sudo apache2ctl -t
```
Should return `Syntax OK`
- if not, check your new conf file and make changes according to the error message returned by apache

Restart apache service: 
```bash
sudo systemctl restart apache2
```

## PHP modules required by nextcloud
There's quite a few of them to load: 
```bash 
sudo apt install php-imagick php7.4-common php7.4-mysql php7.4-fpm php7.4-gd php7.4-json php7.4-curl  php7.4-zip php7.4-xml php7.4-mbstring php7.4-bz2 php7.4-intl php7.4-bcmath php7.4-gmp
```
We have to reload apache again for the changes to take affect: 
```bash
sudo system reload apache2
```

## Set up SSL for Nextcloud/apache
I don't own the domain for my nextcloud, I use a self signed cert for mine. You could use something like LetsEncryp to also get a SSL Cert for nextcloud

Selfsigned: 
```bash
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/apache-selfsigned.key -out /etc/ssl/certs/apache-selfsigned.crt
```
This will set up a propt for you to fill out the self signed cert. The most important line is the one that requests the `Common Name`. You need to enter either the hostname you’ll use to access the server by, or the public IP of the server. It’s important that this field matches whatever you’ll put into your browser’s address bar to access the site, as a mismatch will cause more security errors.

I changed my Virtual host config for my `nextcloud.conf` created earlier, adding this information and changing the port apache is listening on to `443` for SSL
```xml
<VirtualHost *:443>
   ServerName your_domain_or_ip
   DocumentRoot /var/www/your_domain_or_ip

   Header always set Strict-Transport-Security "max-age=31536000"
   SSLEngine on
   SSLCertificateFile /etc/ssl/certs/apache-selfsigned.crt
   SSLCertificateKeyFile /etc/ssl/private/apache-selfsigned.key
</VirtualHost>
```
Then I told apache to redirect requests on port 80 to use SSL, added to the bottom of the `nextcloud.conf` file
```xml
<VirtualHost *:80>
    ServerName your_domain_or_ip
    Redirect / https://your_domain_or_ip/
</VirtualHost>
```

Close the file and test apache config again
```bash
sudo apache2ctl -t
```
RELOAD apache, I missed this part and had quite the headache of `HTTP 500` errors for about 30min (previously I was restarting apache)
```
sudo systemctl reload apache2
```

## Finalize Nextcloud setup via web browser
Now we can access Nextcloud over a secure connection and finalize it's setup. It's availabe at your domain name for it or, if local, at `your-server-ip/nextcloud/`

You will be prompted to set up an admin user and password, chose nextcloud's datafolder and connect nextcloud to the database we created for it earlier, using the user and password we also created for it earlier in MariaDB. 

Click Finish Setup at the bottom and be patient, nextcloud will take a few moments to finalize it's setup. 

## Tuning Nextcloud
After Nextcloud has set itself up, log in and click on your user in the top right, go to settings in the drop down menu. 

You will see your personal settings on the left hand side, and Administration under that. The first option under Administration should be Overview, click on that one

This menu will have Security & Setup warnings at the top. It will tell you what needs to be tuned for Nextcloud. 
ie. Mine had a few, the PHP overflow_buffer was enabled and it shouldn't be, the PHP memory limit was less than 512MB and no memcache was configured for nextcloud. 

The PHP issues are fixed in the PHP.conf file for apache, find the name for them and set according to Nextclouds reccomendations. Set overflow_buffer to off and add memory to the limit if need be. 
```bash
sudo nano /etc/php/7.4/apache2/php.ini
```

## Memcache setup
I used APCu and Redis for a memcache and have excellent performance with my nextcloud. Previously I was using the basic memecache and the performance was better than not having a memcache configured but not as great as APCU and Redis. 

### APCu

For Ubuntu, install APCu via; 
```bash
sudo apt-get install php-apcu
```
Really simple, basically sets itself up, just have to point the nextcloud config.php file to APCu  
Restart the Webserver and add this to `config.php`
```php
'memcache.local' => 'OC\Memcache\APCu',
```
>APCu is disabled by default on CLI which could cause issues with nextcloud’s cron jobs. Please make sure you set the apc.enable_cli to 1 on your php.ini config file or append --define apc.enable_cli=1 to the cron job call.  

### Redis

Install via: 
```bash 
sudo apt-get install redis-server
```
Redis setup requires some configuration for Ubuntu. Open up the redis.conf file with a text editor: 
```bash 
sudo nano /etc/redis/redis.conf
```
Inside the file, find the `supervised` directive. This directive allows you to declare an init system to manage Redis as a service, providing you with more control over its operation. The `supervised` directive is set to `no` by default. Since we are running Ubuntu, which uses the systemd init system, change this to `systemd`:

```conf
# If you run Redis from upstart or systemd, Redis can interact with your
# supervision tree. Options:
#   supervised no      - no supervision interaction
#   supervised upstart - signal upstart by putting Redis into SIGSTOP mode
#   supervised systemd - signal systemd by writing READY=1 to $NOTIFY_SOCKET
#   supervised auto    - detect upstart or systemd method based on
#                        UPSTART_JOB or NOTIFY_SOCKET environment variables
# Note: these supervision methods only signal "process is ready."
#       They do not enable continuous liveness pings back to your supervisor.
supervised systemd
```
Next we need to update the unix socket settings and port, Socket settings are also disabled by default. 
```conf
# Accept connections on the specified port, default is 6379 (IANA #815344).
# If port 0 is specified redis will not listen on a TCP socket
port = 0

...

# Unix Socket.
# Specifiy the path for the Unix socket that will be used to listen for incoming connections
# There is no default, so Redis will not listen 
# on a unix socket when not specified
unixsocket /var/run/redis/redis-server.sock
unixsocket perm 770

...
```

That should get redis ready to listen for nextcloud. We need to now give the www-data user permissions to use Redis for Read/Write
```bash
usermod -a -G redis www-data
```
> This didn't work directly for me, was still hitting a 500 server error after this. I edited my /etc/group file directly to show the following: 
```bash
redis:x:110:www-data
```
was previously `redis:x:119:www-data`

Add Redis to the `nextcloud.conf` file: 
```PHP
'memcache.local' => '\OC\Memcache\APCu',
'memcache.distributed' => '\OC\Memcache\Redis',
'memcache.locking' => '\OC\Memcache\Redis',
'redis' => [
     'host'     => '/run/redis/redis-server.sock',
     'port'     => 0,
],
```

Restart apache server again
```bash
systemctl restart apache2
```
The memcache warnings should now dissappear. 

Redis can be further configured if you wish, look at their [docs](redis.io/documentation) for more

## Conclusion
Nextcloud is now set up and properly configured.  
If there are other warnings they might be specific to your nextcloud configuration, consult google/Nextcloud documentation for more help.  

## References: 
- https://www.linuxbabe.com/ubuntu/install-nextcloud-ubuntu-20-04-apache-lamp-stack
- https://www.digitalocean.com/community/tutorials/how-to-install-mariadb-on-ubuntu-20-04
- https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-redis-on-ubuntu-18-04
- https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-apache-in-ubuntu-20-04 
- https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/caching_configuration.html
- https://redis.io/documentation 
- https://docs.nextcloud.com/server/latest/admin_manual/ 