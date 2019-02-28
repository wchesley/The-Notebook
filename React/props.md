# Props in React

## `{...props}`

It's called spread attributes and its aim is to make the passing of props easier.

Let us imagine that you have a component that accepts _N_ number of properties. 
Passing these down can be tedious and unwieldy if the number grows.

```reactjs
<Component x={} y={} z={} />
```

Thus instead you do this, wrap them up in an object and use the spread notation

```reactjs
var props = { x: 1, y: 1, z:1 };
<Component {...props} />
```

which will unpack it into the props on your component, i.e., you "never" use `{... props}` inside your `render()` function, only when you pass the props down to another component. 
Use your unpacked props as normal `this.props.x`.
