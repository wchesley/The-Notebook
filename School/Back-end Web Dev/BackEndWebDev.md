# Back End web Dev
> WTAMU-CIDM 4382 - Fall 2019
> 08/28/2019

Book can be located [here](https://livebook.manning.com/book/getting-mean-with-mongo-express-angular-and-node/chapter-1)

## Getting MEAN Chapter 01

back end web dev class but really it's more full stack. 

MEAN
* MongoDB - The database; document datastore, largely used to store JSON Like objects
* Express - Backend Framework - Node web server enviroment 
* Angular - FrontEnd framework - Interchageable with ReactJS
* Node - Web server and server-side code execution enviroment
* Why? - End to end javascript (cause you don't know enough already)

assignment 0 is a micro clone of https://www.name-generator.org.uk
     not as complex as this, can dumb it down a bit, I am thinking one input and see what rhymes with that? will need
     rhyming database? CSS optional; example on CodePen.io userID: Jeffry Babb

Assignment 1 will be a modified version of CH4 code found [in this repo](https://github.com/simonholmes/getting-MEAN.git) >Note, there are several branches foreach chapter, make sure you select the correct one  
instead of loc8tr we'll find pizza places.
`git clone -b chapter-04 https://github.com/simonholmes/getting-MEAN.git`  

>Full Assignment Requirements  
## Assignment 1 - Starting Out with Node, Express, and Pug

Chapters 3 and 4 in Simon Holmes' book start out with the basic version of our author's example app: loc8r.

It is imperative that you work through these chapters methodically.  Among the things you'll learn are:

* Installing Node and NPM
* Installing Express
* Utilizing Pug
* Transforming the basic Express project template into an MVC template
     * Creating Pug template views
     * Creating controllers to work with routing and logic
* What does MVC mean? - Model View Controller
* Using Git (and for us, Github)
* Deploying to Heroku

### Tasks

Near the end of chapter four, Simon shows us two important things:

* how to work with mixins and includes to develop reusable aspects of your Pug templates
* how to work with data within your Pug template

What we need to do is modify Simon's code to create a different list of items (rather than locations for wifi).  Here is what you need to do:

* Obtain Simon's chapter 4 code and git pull or download it.
* Modify the code to include an additional list page of three (3) select pizza restaurants in Amarillo and/or Canyon (this means another tab in the navigation for the pizza places)
* Modify the code to develop attributes for each restaurant (they will be different than what Simon uses for locations).
* Modify and/or Copy and Modify the layout.pug, location-info.pug, and locations-list.pug files to accomplish these tasks.
* Since Simon is using a 3rd-party Bootstrap theme, you should do so as well.  The results may not be what you expect, but I want you to experiment
* Create an additional mixin that will also shade the background of each item in the locations-list for your pizza restaurants different colors depending on their rating.

### What to Submit

You will submit the following:

    1. Your Github URL of the repository you make for this project
    1. Your C9 project URL
    1. Your Heroku app URL
    1. Your Express Project ZIPPED up and submitted here.

---
## Babb's project
#### Rough notes, nothing officiall assigned yet
status.vatsim.org? - Babb's project - check his repo
define schema by clienttype - Pilot or Controller. 
Some data points are only defined for pilots and not controllers. 
some data points are shared by each clienttype. 
controllers have a rating, pilots might? 
only points have transponder, 
anything beginning wiht plan is all pilots stuff
only controllers has ATIS message. 

###### 11/11/2019

Read chapter 9 and finish chapter 8 by wednesday. 
Final project requires third party api?! wtf, whyyyyyyyyyy???? it's not needed in my case, using a third party api, to me is just replicating whats already been done. 
I wanted to create an OG api, for my app and consume my data; why do I need another feature or API to tie into this?!  

## Random notes:
###### To be ordered someday 

Getting parameters from `get` request: 
(ref here)[https://stackabuse.com/get-query-strings-and-parameters-in-express-js/]
- **TLDR; it's on `req.query`**   

If request was sent back as param in angulars httpclient it looks something like:  
```javascript
public getSavedRecipe(userID:any): Observable<any> {
    console.log("requested ID:" + userID)
    let params = new HttpParams().set('id', userID)
    return this.httpClient.get('/api/UserRecipes', {params}).pipe(
      map(res => res)
    );
  } 
```
Here is an example of a URL with query strings attached:

`https://stackabuse.com/?page=2&limit=3`
The query parameters are the actual key-value pairs like page and limit with values of 2 and 3, respectively.

Now, let's move on to the first main purpose of this article - how to extract these from our Express request object.

This is a pretty common use-case in Express, and any HTTP server, so hopefully the examples and explanation I show here are clear.

Now, taking the same example from above:

`https://stackabuse.com/?page=2&limit=3`
We'd like to extract both the `page` and `limit` parameters so we know which articles to return to the page that the user requested. While query parameters are typically used in GET requests, it's still possible to see them in POST and DELETE requests, among others.

Your query parameters can be retrieved from the query object on the request object sent to your route. It is in the form of an object in which you can directly access the query parameters you care about. In this case Express handles all of the URL parsing for you and exposes the retrieved parameters as this object.

Let's take a look at an example of us getting query parameters in a route:
```javascript
const express = require('express');
const bodyParser = require('body-parser');
const url = require('url');
const querystring = require('querystring');
const Article = require('./models').Article;

let app = express();
app.use(bodyParser.urlencoded({ extended: false }));
app.use(bodyParser.json());

// Function to handle the root path
app.get('/', async function(req, res) {

    // Access the provided 'page' and 'limt' query parameters
    let page = req.query.page;
    let limit = req.query.limit;

    let articles = await Article.findAll().paginate({page: page, limit: limit}).exec();

    // Return the articles to the rendering engine
    res.render('index', {
        articles: articles
    });
});

let server = app.listen(8080, function() {
    console.log('Server is listening on port 8080')
});
```
In the example above, we assume the page and limit parameters always exist. If neither of these parameters are given in the URL, we'd receive undefined for both page and limit instead.
