# getDerivedStateFromProps

Owner: Edwin

- 替代 [UNSAFE_componentWillReceiveProps](notion://www.notion.so/0196c8714e3d4b99a001387c13b74a14?pvs=25)
- 基于 props 改变当前的 state

```jsx
static getDerivedStateFromProps(props: any, state: any) {
	if (props.text === state.text) {
		return { text: "edwin", };
	}
	return null;
}
```