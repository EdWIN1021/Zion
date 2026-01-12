# option-api

# option-api

## 目录

- 
    
    [option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg.png](option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg.png)
    
- 
    
    [option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%201.png](option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%201.png)
    
- 
    
    [option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%202.png](option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%202.png)
    
    - 
        
        [option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%203.png](option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%203.png)
        
    - 
        
        [option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%204.png](option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%204.png)
        
- 
    
    [option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%205.png](option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%205.png)
    
- 
    
    [option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%206.png](option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%206.png)
    
    - 
        
        [option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%207.png](option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%207.png)
        
    - 
        
        [option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%208.png](option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%208.png)
        
    - 
        
        [option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%209.png](option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%209.png)
        
    - 
        
        [option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%2010.png](option-api%20776abc5a6a7142b386eb7c45eab52c21/Transitionsimageimage_KUqRdOuwqg%2010.png)
        

## Router

---

```
import { createRouter, createWebHistory } from 'vue-router';

import Foo from './Bar.vue';
import Bar from '.Foo.vue';

const routes = [
  {
    path: '/foo',
    component: Foo,
  },
  {
    path: '/bar',
    component: Bar,
  },
];

const router = createRouter({
  history: createWebHistory(),
  routes,
  linkActiveClass: 'active',
})

app.use(router);
```

## Router-View

---

```
<template>
  <router-view></router-view>
</template>

```

## Navigation

---

### Router-Link

```
<router-link to="/foo">Foo</router-link>

```

### $router

```
this.$router.push("/bar")
this.$router.back();
this.$router.forward();
```

# Dynamic Route

---

```
    // this.$route.path
    this.$route.params.teamId;
    <router-link :to="`/teams/${id}`">View Members</router-link>
```

# Redirect

---

### redirect

```
const routes = [
  {
     path: '/',
     redirect: '/foo',
  }
]
```

### alias

> 💡does not change the url
> 

```
const routes = [
  {
     path: '/foo',
     component: Foo,
     alias: '/',
  }
]
```

## Not Found

---

```
const routes = [
  {
    path: '/:notFoumd(.*)',
    component: NotFound,
  }
]
```

## Nested Routes

---

```

```

[In-Component Guards](In-Component%20Guards%20bf9154e31eae405685918a1cdf6e0c00.md)