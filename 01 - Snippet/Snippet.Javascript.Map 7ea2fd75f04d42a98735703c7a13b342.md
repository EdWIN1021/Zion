# Map 7ea2fd75f04d42a98735703c7a13b342

Owner: Edwin

# Map

Owner: edwin S

```jsx
var collection = new Map();
collection.set('key1', 'value1');
collection.set('key2', 'value2');
collection.set('key3', 'value3');

collection.size; // 3
collection.get('key4');// undefined
collection.has('key4');// false

collection.delete('key1');
collection.has('key1'); // false

collection.clear();
```

## convert object to map

```jsx
const obj = {
  name: "aaa",
  age: "bbb",
  arr: ["c", "d", "e"],
};

new Map(Object.entries(obj));

// Map(3) { 'name' => 'aaa', 'age' => 'bbb', 'arr' => [ 'c', 'd', 'e' ] }
```

## Looping Map

```jsx
const map = new Map([
  [1, "a"],
  [2, "b"],
  [3, "c"],
  [4, "d"],
]);

for (const i of map) console.log(i);
for (const [key, value] of map)  <= optional

/*
  [ 1, 'a' ]
  [ 2, 'b' ]
  [ 3, 'c' ]
  [ 4, 'd' ]
*/
```

## Convert map to array

```jsx
const map = new Map([
  [1, "a"],
  [2, "b"],
  [3, "c"],
  [4, "d"],
]);

[...map.keys()]
[...map.values()]
```