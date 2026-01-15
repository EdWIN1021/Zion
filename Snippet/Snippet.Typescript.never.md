# never

Owner: Edwin

<aside>
💡 The **`never`** type is often used to annotate functions that throw exceptions or have infinite loops, preventing them from ever returning a value

</aside>

```tsx
function throwError(message: string): never {
  throw new Error(message);
}

function infiniteLoop(): never {
  while (true) {
    // This function never returns
  }
}
```