# interface

Owner: Edwin

- interfaces are typically used when you want to define the `shape of objects` and ensure that a specific `contract` is followed

```tsx
interface PersonContract {
  readonly name: string;
  age: number;
}
```

---

## Extends

```tsx
interface Creature {
  type: string;
  age: number;
}

interface Human extends Creature {
  name: string;
}
```

## Class

```tsx
interface PersonContract {
  name: string;
  age: number;
  greet: (phrase: string) => void;
}

class Person implements PersonContract {
  name: string;
  age: number;
  greet: (phrase: string) => void;
}
```