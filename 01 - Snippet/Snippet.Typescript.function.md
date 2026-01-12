```tsx
function print(): void {
  console.log('void');
}

function add(num1: number, num2: number) {
  return num1 + num2;
}

function add(num1: number, num2: number): number {
  return num1 + num2;
}

const add = (num1: number, num2: number = 1) => {
  return num1 + num2;
};
```

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

```tsx
let add: (num1: number, num2: number) => number;
```