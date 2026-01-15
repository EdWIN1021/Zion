# FlatList

Owner: Edwin

```tsx
<FlatList
  horizontal
  showsHorizontalScrollIndicator={false}
  data={friends}
  renderItem={({ item }) => <Text>{item.name}</Text>}
  keyExtractor={(item) => item.name}
/>
```

---

## **Attributes**

- horizontal
- showsHorizontalScrollIndicator
    - hide scroll bar
- data
- renderItem
- keyExtractor