# rest operator ed23777ce5894c74811f7d5d077905cd

Owner: Edwin

# rest operator

Owner: edwin S

## Array

---

```jsx
const arr = [1, 2, 3, 4, 5, 6];
const [a, b, c, ...rest] = arr;
// rest => [ 4, 5, 6 ]
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

const { name, ...rest } = obj;

/* rest =>
  {
    age: 'bbb',
    arr: [ 'c', 'd', 'e' ],
    time: { mon: { open: 1, close1: 2 } }
  }
*/
```

## Function

```
const arr = [1, 2, 3, 4];

const add = (...nums) => {
  let total = 0;
  for (let i = 0; i < nums.length; i++) {
    total += nums[i];
  }
  console.log(total);
};

add(...arr);

// total => 10
```