# composition-api

# composition-api

## 目录

- 
    
    [composition-api%20967052d9875840ca911a80862111f833/Transitionsimageimage_KUqRdOuwqg.png](composition-api%20967052d9875840ca911a80862111f833/Transitionsimageimage_KUqRdOuwqg.png)
    
- 
    
    [composition-api%20967052d9875840ca911a80862111f833/Transitionsimageimage_KUqRdOuwqg%201.png](composition-api%20967052d9875840ca911a80862111f833/Transitionsimageimage_KUqRdOuwqg%201.png)
    

## useStore

---

```
import { useStore } from 'vuex'
const store = useStore()

```

## computed

---

```
  return {
    foo: computed(() => store.state.foo)
  }
```