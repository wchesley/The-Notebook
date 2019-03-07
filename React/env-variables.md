# Using environment variables in React

###### Adapted from [this article](https://medium.com/@trekinbami/using-environment-variables-in-react-6b0a99d83cf5)

When you don’t have a server-side programming background, environment variables can seem like a bit of magic. That lack of knowledge smacks you in the face like a bag of dicks when you’re done creating todo applications on your localhost, and try to create a production build for the first time.

### The problem we’re solving:
How to declare different API url’s for your local development build and production build
In short: environment variables

When working with React, environment variables are variables that are available through a global `process.env` Object. That global Object is provided by your environment through NodeJs. And because we don’t have NodeJs in the browser, we’re going to need webpack.

## The .env file: 
The whole idea here is to create a file (called just .env) filled with your environment variables. There's a lovely repo that makes this process really easy
Enter [dotenv](https://github.com/motdotla/dotenv)

#### _To prevent people from finding out your local database password is the same one you use for every single one of your accounts on the internet, you *NEED* to add the .env file to your .gitignore._

Your front-end code will refer to the same environment variable (`process.env.API_URL`) on both environments (development/production), but because you defined different values in your `.env files`, the compiled values will be different.

Let’s create an `.env` file
Create a `.env` file in the root directory of your project. Add environment-specific variables on new lines in the form of `NAME=VALUE`. For example:
```.env
DB_HOST=localhost
DB_USER=root
DB_PASS=s1mpl3
```

`process.env` now has the keys and values you defined in your `.env` file.
### Handle the .env file
As early as possible in the app (for react I use /src/index.js) you need to declare
```javascript
require('dotenv').config()
```
Is that is? Yes, that’s it..

Calling `.config()` on dotenv will return an Object with all the environment variables set in your `.env` file under a key called parsed. Now, let’s check our React code:

```javascript
const App = () => <h1>{process.env.API_URL}</h1>;
```

And damn, it works! It shows the value of the `API_URL` environment variable that you defined in your `.env` file.
