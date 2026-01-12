# Set 365379b1b9c24200ac9c270aca61f42a

Owner: Edwin

# Set

Owner: edwin S

```jsx
const set = new Set(["a", "a", "b", "b", "c"]);
// Set(3) { 'a', 'b', 'c' }
```

## With String

```jsx
new Set("aabbc");
// Set(3) { 'a', 'b', 'c' }
```

## Size

```jsx
set.size
// 3
```

## Has

```jsx
set.has("a")
// true
```

## Add

```jsx
set.add("e");
// Set(4) { 'a', 'b', 'c', 'e' }
```

## Delete

```jsx
set.delete("a");
// Set(2) { 'b', 'c' }
```

## Clear

```jsx
set.clear();
// Set(0) {}
```

# Looping Set

---

```jsx
for (const i of set) console.log(i);
/*
  a
  b
  c
*/
```