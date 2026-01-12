# composition-api

# composition-api

## 目录

- 
    
    [composition-api%20f5966adbcad142c58bb70f1b1c59baee/Transitionsimageimage_KUqRdOuwqg.png](composition-api%20f5966adbcad142c58bb70f1b1c59baee/Transitionsimageimage_KUqRdOuwqg.png)
    
- 
    
    [composition-api%20f5966adbcad142c58bb70f1b1c59baee/Transitionsimageimage_KUqRdOuwqg%201.png](composition-api%20f5966adbcad142c58bb70f1b1c59baee/Transitionsimageimage_KUqRdOuwqg%201.png)
    
- 
    
    [composition-api%20f5966adbcad142c58bb70f1b1c59baee/Transitionsimageimage_KUqRdOuwqg%202.png](composition-api%20f5966adbcad142c58bb70f1b1c59baee/Transitionsimageimage_KUqRdOuwqg%202.png)
    
    - 
        
        [composition-api%20f5966adbcad142c58bb70f1b1c59baee/Transitionsimageimage_KUqRdOuwqg%203.png](composition-api%20f5966adbcad142c58bb70f1b1c59baee/Transitionsimageimage_KUqRdOuwqg%203.png)
        

## setup

---

> 💡组件被创建之前执行, 并无法获取任何的组件实例
> 
- 接受prop和context的函数
- 返回的所有内容都暴露給组建的其余部分，例如 methods, computed…

```
components:{},
props:{},
setup(props){
  onMounted()

  return {}
}
```

## ref

---

> 💡创建响应式引用
> 

```
import { ref } from 'vue

setup(props){
  const foo = ref(0);

  const update = () => {
    foo.value = 1
  }
  return { foo, update }
}

```

## reactive

---

> 💡work with Object
> 

```
import { reactive } from 'vue';

setup(props){
  const foo = reactive({
      name: '',
      age: 0,
    });

  const update = () => {
    foo.name = 'bar'
    foo.age = 100
  }
  return { foo, update }
}
```

### compouted

---

```
import { computed, ref } from "vue";

setup(props){
  const firstName = ref('');
  const lastName = ref('');

  const fullName = computed(()=> firstName.value + lastName.value)

  return { lastName, firstName, fullName }
}
```

[Emitted Events](Emitted%20Events%20a67bd8f10dcd4cccbeaccb2cfb0aee0b.md)

[ref](ref%2080445df4d68d4d3cbd5459ad526d75fa.md)