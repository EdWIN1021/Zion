# types

## reactive

```tsx
interface Book {
  title: string
  year?: number
}

const book:Book = reactive({title: "foo"})
```

## refs

```tsx
const year = ref<string | number>('2020')

```

## computed

```tsx
const double = computed<number>(() => {
  // type error if this doesn't return a number
})
```