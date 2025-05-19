## Value of `this` in a node module:

`this` in NodeJS **global scope** is the current module.exports object, not the global object. This is different from a browser where the global scope is the global `window` object. Consider the following code executed in Node:

```javascript
console.log(this);    // logs {}

module.exports.foo = 5;

console.log(this);   // log { foo:5 }
```

First we log an empty object because there are no values in `module.exports` in this module. Then we put `foo` on the `module.exports` object, when we then again log `this` we can see that it now logs the updated `module.exports` object.

## How can we access the `global` object:

We can access the `global` object in node using the `global` keyword:

```javascript
console.log(global);
```

The `global` object exposes a variety of useful properties about the environment. Also this is the place where functions as `setImmediate` and `clearTimeout` are located.