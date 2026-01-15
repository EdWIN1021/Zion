# spread operator

Owner: Edwin

## Array

---

```jsx
const arr = [1, 2, 3];
const new_arr = [...arr];
// new_arr => [ 1, 2, 3 ]

console.log(...new_arr);
// 1, 2, 3
```

## Object

---

```jsx
const obj = {
  name: "aaa",
  age: "bbb",
  arr: ["c", "d", "e"],
  time: {
    mon: {
      open: 1,
      close1: 2,
    },
  },
};

const new_obj = { ...obj, location: "zzz" };

/*new_obj =>
 {
  name: 'aaa',
  age: 'bbb',
  arr: [ 'c', 'd', 'e' ],
  time: { mon: { open: 1, close1: 2 } },
  location: 'zzz'
}
*/

```

```tsx
const sum = (...numbers: number[]) => {
  return numbers.reduce((acc, curr) => acc + curr, 0);
};

sum(1, 2, 3, 4, 5);
```