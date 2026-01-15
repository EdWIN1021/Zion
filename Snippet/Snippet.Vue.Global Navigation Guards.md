# Global Navigation Guards

## beforeEach

> 💡Global before guards are called in creation order, whenever a navigation is triggered.
> 

```jsx
router.beforeEach((to, from) => {  return false})
```

## beforeResolve

> 💡after all in-component guards and async route components are resolved
> 

```jsx
router.beforeResolve((to, from) => {});
```

## afterEach

> 💡afterEach
> 

```jsx
router.afterEach((to, from) => {})
```

## Per-Route Guard

> 💡You can define beforeEnter guards directly on a route’s configuration object
> 

```jsx
const routes = [  {    path: '/users/:id',    component: UserDetails,    beforeEnter: (to, from) => {      // reject the navigation      return false    },  },]
```