# React Router

Basics on installing react router to an application, minor use cases covered. <br>Please see [here](https://blog.pshrmn.com/entry/simple-react-router-v4-tutorial/) for more information

## Installation
React Router has been broken into three packages: `react-router`, `react-router-dom`, and `react-router-native`.

You should almost never have to install `react-router` directly. That package provides the core routing components and functions for React Router applications. The other two provide environment specific (browser and React Native) components, but they both also re-export all of react-router's exports.

Install via: 
`npm install --save react-router-dom`

## Rendering a `<Router>`
Router components only expect to receive a single child element. To work within this limitation, it is useful to create an <App> component that renders the rest of your application. Separating your application from the router is also useful for server rendering because you can re-use the <App> on the server while switching the router to a <MemoryRouter>.

```JS
import { BrowserRouter } from 'react-router-dom';

ReactDOM.render((
  <BrowserRouter>
    <App />
  </BrowserRouter>
), document.getElementById('root'));
```

Now that we have implemented our router, we can start to render our actual application.

## The <App>
Our application is defined within the <App> component. To simplify things, we will split our application into two parts. The <Header> component will contain links to navigate throughout the website. The <Main> component is where the rest of the content will be rendered.

```js
// this component will be rendered by our <___Router>
function App() {
  return (
    <div>
      <Header />
      <Main />
    </div>
  );
}
```

###### Note: You can layout your application any way that you would like, but separating routes and navigation makes it easier to show how React Router works for this tutorial.

We will define the content in the <Main> component first. This is where we will render our routes.

## Routes
The <Route> component is the main building block of React Router. Anywhere that you want to only render content based on the location’s pathname, you should use a <Route> element.

### Path
A <Route> expects a path prop, which is a string that describes the pathname that the route matches — for example, <Route path='/roster'/> should match a pathname that begins with /roster 2. When the current location’s pathname is matched by the path, the route will render a React element. When the path does not match, the route will not render anything 3.

```JS
<Route path='/roster'/>
// when the pathname is '/', the path does not match
// when the pathname is '/roster' or '/roster/2', the path matches
// If you only want to match '/roster', then you need to use
// the "exact" prop. The following will match '/roster', but not
// '/roster/2'.
<Route exact path='/roster'/>
// You might find yourself adding the exact prop to most routes.
// In the future (i.e. v5), the exact prop will likely be true by
// default. For more information on that, you can check out this 
// GitHub issue:
// https://github.com/ReactTraining/react-router/issues/4958
```

###### Note: When it comes to matching routes, React Router only cares about the pathname of a location. That means that given the URL:

http://www.example.com/my-projects/one?extra=false
the only part that React Router attempts to match is /my-projects/one.

### Matching paths
React Router uses the path-to-regexp package to determine if a route element’s path prop matches the current location. It compiles the path string into a regular expression, which will be matched against the location’s pathname. path strings have more advanced formatting options than will be covered here. You can read about them in the path-to-regexp documentation.

When the route’s path matches, a match object with the following properties will be created:

* url   the matched part of the current location’s pathname
* path	the route's path
* isExact	path === pathname
* params	an object containing values from the pathname that were captured by path-to-regexp
* You can use this route tester to play around with matching routes to URLs.

Note: Currently, a route’s path must be absolute 4.

## Creating our routes
<Route>s can be created anywhere inside of the router, but often it makes sense to render them in the same place. You can use the <Switch> component to group <Route>s. The <Switch> will iterate over its children elements (the routes) and only render the first one that matches the current pathname.

For this website, the paths that we want to match are:

/	the homepage
/roster	the team’s roster
/roster/:number	a profile for a player, using the player’s number
/schedule	the team’s schedule of games
In order to match a path in our application, all that we have to do is create a <Route> element with the path prop we want to match.

```js
<Switch>
  <Route exact path='/' component={Home}/>
  {/* both /roster and /roster/:number begin with /roster */}
  <Route path='/roster' component={Roster}/>
  <Route path='/schedule' component={Schedule}/>
</Switch>
```
What does the <Route> render?
Routes have three props that can be used to define what should be rendered when the route’s path matches. Only one should be provided to a <Route> element.

component — A React component. When a route with a component prop matches, the route will return a new element whose type is the provided React component (created using React.createElement).
render — A function that returns a React element 5. It will be called when the path matches. This is similar to component, but is useful for inline rendering and passing extra props to the element.
children — A function that returns a React element. Unlike the prior two props, this will always be rendered, regardless of whether the route’s path matches the current location.
```js
<Route path='/page' component={Page} />
const extraProps = { color: 'red' }
<Route path='/page' render={(props) => (
  <Page {...props} data={extraProps}/>
)}/>
<Route path='/page' children={(props) => (
  props.match
    ? <Page {...props}/>
    : <EmptyPage {...props}/>
)}/>
```
Typically, either the component or render prop should be used. The children prop can be useful occasionally, but typically it is preferable to render nothing when the path does not match. We do not have any extra props to pass to the components, so each of our <Route>s will use the component prop.

The element rendered by the <Route> will be passed a number of props. These will be the match object, the current location object 6, and the history object (the one created by our router) 7.

<Main>
Now that we have figured our root route structure, we just need to actually render our routes. For this application, we will render our <Switch> and <Route>s inside of our <Main> component, which will place the HTML generated by a matched route inside of a <main> DOM node.

```js
import { Switch, Route } from 'react-router-dom'
function Main() {
  return (
    <main>
      <Switch>
        <Route exact path='/' component={Home}/>
        <Route path='/roster' component={Roster}/>
        <Route path='/schedule' component={Schedule}/>
      </Switch>
    </main>
  );
}
```

Note: The route for the homepage includes an exact prop. This is used to state that that route should only match when the pathname matches the route’s path exactly.

### Nested Routes
The player profile route /roster/:number is not included in the above <Switch>. Instead, it will be rendered by the <Roster> component, which is rendered whenever the pathname begins with /roster.

Within the <Roster> component we will render routes for two paths:

```js
/roster — This should only be matched when the pathname is exactly /roster, so we should also give that route element the exact prop.
/roster/:number — This route uses a path param to capture the part of the pathname that comes after /roster.
function Roster() {
  return (
    <Switch>
      <Route exact path='/roster' component={FullRoster}/>
      <Route path='/roster/:number' component={Player}/>
    </Switch>
  );
}
```
It can be useful to group routes that share a common prefix in the same component. This allows for simpler parent routes and gives us a place to render content that is common across all routes with the same prefix.

As an example, <Roster> could render a title that would be displayed for all routes whose path begins with /roster.

```js
function Roster() {
  return (
    <div>
      <h2>This is a roster page!</h2>
      <Switch>
        <Route exact path='/roster' component={FullRoster}/>
        <Route path='/roster/:number' component={Player}/>
      </Switch>
    </div>
  );
}
```

## Path Params
Sometimes there are variables within a pathname that we want to capture. For example, with our player profile route, we want to capture the player’s number. We can do this by adding path params to our route’s path string.

The :number part of the path /roster/:number means that the part of the pathname that comes after /roster/ will be captured and stored as match.params.number. For example, the pathname /roster/6 will generate a params object:

```js
{ number: '6' } // note that the captured value is a string
The <Player> component can use the props.match.params object to determine which player’s data should be rendered.

// an API that returns a player object
import PlayerAPI from './PlayerAPI'
function Player(props) {
  const player = PlayerAPI.get(
    parseInt(props.match.params.number, 10)
  )
  if (!player) {
    return <div>Sorry, but the player was not found</div>
  }
  return (
    <div>
      <h1>{player.name} (#{player.number})</h1>
      <h2>{player.position}</h2>
    </div>
  );
}
```

You can learn more about path params in the path-to-regexp documentation.

Alongside the <Player> component, our website also includes <FullRoster>, <Schedule>, and <Home> components.

```js
function FullRoster() {
  return (
    <div>
      <ul>
        {
          PlayerAPI.all().map(p => (
            <li key={p.number}>
              <Link to={`/roster/${p.number}`}>{p.name}</Link>
            </li>
          ))
        }
      </ul>
    </div>
  );
}

function Schedule() {
  return (
    <div>
      <ul>
        <li>6/5 @ Evergreens</li>
        <li>6/8 vs Kickers</li>
        <li>6/14 @ United</li>
      </ul>
    </div>
  );
}

function Home() {
  return (
    <div>
      <h1>Welcome to the Tornadoes Website!</h1>
    </div>
  );
}
```

## Links
Finally, our application needs a way to navigate between pages. If we were to create links using anchor elements, clicking on them would cause the whole page to reload. React Router provides a <Link> component to prevent that from happening. When clicking a <Link>, the URL will be updated and the rendered content will change without reloading the page.

```js
import { Link } from 'react-router-dom'
function Header() {
  return (
    <header>
      <nav>
        <ul>
          <li><Link to='/'>Home</Link></li>
          <li><Link to='/roster'>Roster</Link></li>
          <li><Link to='/schedule'>Schedule</Link></li>
        </ul>
      </nav>
    </header>
  );
}
```
<Link>s use the to prop to describe the location that they should navigate to. This can either be a string or a location object (containing a combination of pathname, search, hash, and state properties). When it is a string, it will be converted to a location object.

<Link to={{ pathname: '/roster/7' }}>Player #7</Link>
Note: Currently, a link's pathname must be absolute

## Annotations
1. Locations are objects with properties to describe the different parts of a URL:
```JS
// a basic location object
  { pathname: '/', search: '', hash: '', key: 'abc123' state: {} }
```
2. You can render a pathless <Route>, which will match every location. This can be useful for accessing methods and variables that are stored in the context.

1. If you use the children prop, the route will render even when its path does not match the current location.

1. There is work being done to add support for relative <Route>s and <Link>s. Relative <Link>s are more complicated than they might initially seem to be because they should be resolved using their parent match object, not the current URL.

1. This is essentially a function component. Internally, the big difference between the components passed to component and render is that component will use React.createElement to create the element, while render will call the component as a function. If you were to define an inline function and pass it to the component prop, it would be much slower than using the render prop. 
```JS
<Route path='/one' component={One}/>
  // React.createElement(props.component)
  <Route path='/two' render={() => <Two />}/>
  // props.render()
  ```
6. The <Route> and <Switch> components can both take a location prop. This allows them to be matched using a location that is different than the actual location (the current URL).

1. They are also passed a staticContext prop, but that is only useful when doing server side rendering.
 