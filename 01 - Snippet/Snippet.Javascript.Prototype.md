# Prototype

Owner: Edwin

<aside>
💡 All objects created using a constructor function or a class have a prototype property.

</aside>

### 3 ways of create prototype

- Constructor functions
- ES6 Class
- [Object.create](https://www.notion.so/d2a41847e25343799c3a47370d8a89cb?pvs=21)

- All Objects inherit properties and methods from prototype
- Object.prototype is on the top of the prototype inheritance chain
- Prototype property allows add new properties and method to constructors

- Function object has .__proto__ and .prototype properties
    - .__proto__ points to the Function.prototype object
- object created by object literal does not have .prototype property, it has .__proto__

### Prototype property

```jsx
function Person(name) {
  this.name = name;
}

// Person.prototype object is also created by Person constructor
```

### Prototype chain

![Screenshot 2023-11-15 at 1.35.45 PM.png](Prototype%201de11f5a0bd446a998f924e714672a94/Screenshot_2023-11-15_at_1.35.45_PM.png)