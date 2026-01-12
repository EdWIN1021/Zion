# function

Owner: Edwin

```tsx
function merge<T, U>(objA: T, objB: U) {
  return Object.assign(objA, objB);
}

const mergedObj = merge<{ name: string }, { age: number }>(
  { name: "edwin" },
  { age: 100 }
);
```

```tsx
function merge<T extends object, U extends object>(objA: T, objB: U) {
  return Object.assign(objA, objB);
}

const mergedObj = merge({ name: 'edwin' }, { age: 100 });
```

```tsx
function doSomthing<T extends object, U extends keyof T>(obj: T, key: U) {
  return obj[key];
}
```