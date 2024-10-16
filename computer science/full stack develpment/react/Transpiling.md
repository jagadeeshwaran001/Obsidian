Process of converting [[JSX]] into [[html]] by Transpiler [[React]] is [[Transpiling]]


[[babel]] is the transpiler for the [[React]]


eg:

```js
function Heading(props) {
    return <h1>{props.title}</h1>
}
```

this is transpiled as classic in [[babel]] below

```js
function Heading(props) {
  return /*#__PURE__*/React.createElement("h1", null, props.title);
}
```

on the above example `createElement()` has 3 args
1. [[DOM]] element to render
2. The second property is any HTML attribute that should be added, and there's a null here - meaning, there should be an object with some data, but there isn't any data so instead of the object there's the null value.
3. The third property is the contents of the inner HTML of the DOM element specified as the first argument - in this case, the contents of the inner HTML of the h1 element.

