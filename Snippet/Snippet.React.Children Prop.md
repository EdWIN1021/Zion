# Children Prop

Owner: Edwin

- The **`props.children`** syntax allows you to include arbitrary content within a component, making it versatile for different use cases and facilitating the composition of complex user interfaces.

```jsx
const Button: React.FC<{ children: React.ReactNode }> = ({ children }) => {
	return <button>{children}</button>;
};
```