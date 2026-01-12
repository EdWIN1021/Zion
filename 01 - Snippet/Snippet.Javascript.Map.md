

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