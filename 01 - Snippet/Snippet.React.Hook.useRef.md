# useRef

Owner: Edwin

<aside>
💡 A Object with a mutable .current property that is persisted across renders.

</aside>

- [Example](https://github.com/EdWIN1021/react_cheatsheet/blob/function/hooks/useRef/src/App.tsx)
- Creating a variable that stays the same between renders.
    - setTimeout
- Updating refs does not causes re-render
- Selecting and storing DOM elements.

## DOM

```jsx
const inputField = useRef() as MutableRefObject<HTMLInputElement>;

<input ref={inputField} />
```

```tsx
const cardRef = useRef() as MutableRefObject<HTMLDivElement>;
```

## Variable

```jsx
const countRef = useRef(100);
```