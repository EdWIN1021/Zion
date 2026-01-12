# types

# types

## 目录

- 
    
    [types%20eed3d88faf1b41bb952e69bb96899643/Transitionsimageimage_KUqRdOuwqg.png](types%20eed3d88faf1b41bb952e69bb96899643/Transitionsimageimage_KUqRdOuwqg.png)
    
- 
    
    [types%20eed3d88faf1b41bb952e69bb96899643/Transitionsimageimage_KUqRdOuwqg%201.png](types%20eed3d88faf1b41bb952e69bb96899643/Transitionsimageimage_KUqRdOuwqg%201.png)
    
- 
    
    [types%20eed3d88faf1b41bb952e69bb96899643/Transitionsimageimage_KUqRdOuwqg%202.png](types%20eed3d88faf1b41bb952e69bb96899643/Transitionsimageimage_KUqRdOuwqg%202.png)
    

---

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