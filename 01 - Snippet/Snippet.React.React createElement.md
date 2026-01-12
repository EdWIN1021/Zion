# React.createElement

Owner: Edwin

- React.createElement(type, [props], [...children])
- React elements are virtual representations of UI components that describe what should be rendered in the browser.

```jsx
const element = React.createElement(
	'h1', 
	{ className: 'greeting' }, 
	'Hello, World!'
);
```