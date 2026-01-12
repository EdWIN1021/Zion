# Global Navigation Guards

# Global Navigation Guards

## 目录

- 
    
    [Global%20Navigation%20Guards%20e4f89ad3b2c94a748709d73e4247b1f5/Transitionsimageimage_KUqRdOuwqg.png](Global%20Navigation%20Guards%20e4f89ad3b2c94a748709d73e4247b1f5/Transitionsimageimage_KUqRdOuwqg.png)
    
- 
    
    [Global%20Navigation%20Guards%20e4f89ad3b2c94a748709d73e4247b1f5/Transitionsimageimage_KUqRdOuwqg%201.png](Global%20Navigation%20Guards%20e4f89ad3b2c94a748709d73e4247b1f5/Transitionsimageimage_KUqRdOuwqg%201.png)
    
- 
    
    [Global%20Navigation%20Guards%20e4f89ad3b2c94a748709d73e4247b1f5/Transitionsimageimage_KUqRdOuwqg%202.png](Global%20Navigation%20Guards%20e4f89ad3b2c94a748709d73e4247b1f5/Transitionsimageimage_KUqRdOuwqg%202.png)
    
- 
    
    [Global%20Navigation%20Guards%20e4f89ad3b2c94a748709d73e4247b1f5/Transitionsimageimage_KUqRdOuwqg%203.png](Global%20Navigation%20Guards%20e4f89ad3b2c94a748709d73e4247b1f5/Transitionsimageimage_KUqRdOuwqg%203.png)
    

---

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