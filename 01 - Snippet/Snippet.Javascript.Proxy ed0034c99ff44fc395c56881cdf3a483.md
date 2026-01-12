# Proxy ed0034c99ff44fc395c56881cdf3a483

Owner: Edwin

# Proxy

Owner: edwin S

- E6
- 拦截机制，对外界对象的访问进行过滤和改写

```jsx
let obj = {};
let handler = {
  get(target, property) {
    console.log(`getter: ${property}`);
    return target[property];
  },
  set(target, property, value) {
    console.log(`setter: ${property} =  ${value}`);
    target[property] = "hello " + value;
  },
};
const p = new Proxy(obj, handler);
p.name = "edwin";
p.name;
```