# Emitted Events

# Emitted Events

---

> 💡Emitted event can be explicitly declared on the component via the definEmits() macro
> 

```
import { defineEmits } from "vue";
```

- parent
    - template
        
        ```
        <MyComponent @someEvent="callback" />
        ```
        
- child
    - template
        
        ```
        <button @click="$emit('someEvent')">click</button>
        ```
        
    - script
        
        ```
        const emit = defineEmits(['someEvent'])
        emit('someEvent')
        ```