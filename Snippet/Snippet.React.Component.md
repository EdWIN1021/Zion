# Component

Owner: Edwin

![Screenshot 2023-11-09 at 10.09.11 AM.png](Component%204335a3ff5ff84641b62e07e2cfb5cdd8/Screenshot_2023-11-09_at_10.09.11_AM.png)

## Component

- A component is a function that returns React elements, usually written as JSX

## Instance

- Instance are created when we use components
- Has its own state and props
- Has a lifecycle
- [React.createElement](React%20createElement%20e8cee727f2744fbf8ac4ee1b9acf1237.md) function calls

## Side Effect

- dependency on or modification of any data outside the function scope.
- Mutating external variables, Http requests, writing to DOM

## Pure Function

- a function that has no side effects.
- same input, always returns the same input.

```jsx
function circleArea(r){
	return 3.14 * r * r;
}
```

## Pure Components (Render Logic)

- given the same props (input), a component instance should always return the same JSX (output).
- Must produce no side effects.
    - Do not perform network request.
    - Do not start timers
    - Do not directly use DOM API
    - Do not mutate objects or variable outside of the function scope.
    - Do not update state or refs
- Side effects are allowed in event handler functions.