# useState

Owner: Edwin

- 返回一对值 state, setState
- 不会合并新的和旧的state

## Update State with Callback Function

```jsx
setUserInput((prevState) => {
	return { ...prevState, [event.target.name]: event.target.value };
 });
```

## Initial State with Callback Function

```jsx
const [token, setToken] = useState(()=> localStorage.getItem('jwt'))
```