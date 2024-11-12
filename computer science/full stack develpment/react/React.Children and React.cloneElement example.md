

```jsx
const Row = ({children, spacing}) => {
	const childStyle = {
		marginLeft: `${spacing}px`,
	};

	return(
		<div>
			{React.Children.map(children, (child, index) => {
				return React.cloneElement(child, {
					style: {
						...child.props.style,
						...(index > 0 ? childStyle : {}),
					},
				});
			})}
		</div>
	)
}
```