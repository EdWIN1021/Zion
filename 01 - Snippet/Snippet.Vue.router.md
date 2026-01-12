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