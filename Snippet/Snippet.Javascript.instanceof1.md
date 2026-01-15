# instanceof

Owner: Edwin

# instanceof

- 判段在其原型链中能否找到该类型的原型

```jsx
2 instanceof Number                   // false
true instanceof Boolean               // false
'str' instanceof String               // false
[] instanceof Array                   // true
function(){} instanceof Function      // true
{} instanceof Object
```