# function

Owner: Edwin

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