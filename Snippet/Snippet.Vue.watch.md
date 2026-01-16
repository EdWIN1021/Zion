## options

```
data(){
  value:""
}

watch:{
  value(newValue, oldValue){
    //do something
  }
}
```

## composition

```
import { ref, watch } from 'vue';

const value = ref('')

watch:{
  value(newValue, oldValue){
    //do something
  }
}

```