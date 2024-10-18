In [[React]] props is a special keyword what stands for properties and is used to passing data from one component to another.

It is uni directional it can only send from parent to child.

in react we cannot modify the props it can never define the props values in that component.

eg:
```jsx
function Heading(props) {
	props.title = "new Value"; //not allowed
	return(
		<h1>{props.title}</h1>
	);
};
```
