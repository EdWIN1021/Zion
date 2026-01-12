
> 💡Writing ! after any expression is effectively a type assertion that the value isn’t null or undefined: 

```tsx
function liveDangerously(x?: number | null) {
  console.log(x!.toFixed());
}
```