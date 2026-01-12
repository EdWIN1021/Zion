# Destructuring assignment

Owner: Edwin

```jsx
const arr = ["a", "b", "c"];
const [x, y, z] = arr;
// a b c
```

```jsx
const arr = ["a", "b", "c", ["e", "f"]];
const [, , , x] = arr;
// [ 'e', 'f' ]
```

```jsx
const obj = {
  name: "aaa",
  age: "bbb",
  arr: ["c", "d", "e"],
  time: {
    mon: {
      open: 1,
      close: 2,
    },
  },
};

const {name, time: { mon }, arr} = obj;

// name => aaa time.mon=> 1 arr[0] =>c
```