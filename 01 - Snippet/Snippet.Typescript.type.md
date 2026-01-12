# type

Owner: Edwin

- type aliases are more flexible and better suited for defining `complex types`, `union types`, `intersection types`, and for improving code readability.

```tsx
type Point = {
    x:number
    y:number
}
```

## Union

```tsx
type ID  = number | string;
```

---

## Intersection

```tsx
type Type1 = { prop1: string };
type Type2 = { prop2: number };

type CombinedType = Type1 & Type2;
```