## Hoisting

Hoisting is a behavior in JavaScript where variable and function declarations are moved to the top of their containing scope during the compilation phase, before the code is executed.

### undefined vs not defined
```js
// undefined 
console.log(a);
var a = "foo";

// Cannot access 'a' before initialization const a = "qwe";
console.log(a); 
var a = "bar"; 
```

### TDZ (Temporal Dead Zone)
<img width="907" alt="Screenshot 2023-10-23 at 3 34 13 PM" src="https://github.com/EdWIN1021/cheatsheet/assets/17692914/dfff4820-223f-4fda-901a-887eff937d0c">
