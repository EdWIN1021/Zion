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

## useRouter

```
  import { useRouter } from 'vue-router'
  const router = useRouter()

  router.push('/')
```

## useRoute

> 💡The route object is a reactive object,
> 

```
import { useRoute } from 'vue-router'
const route = useRoute()

route.params
```

## useLink

> 💡
> 

[## setup

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

