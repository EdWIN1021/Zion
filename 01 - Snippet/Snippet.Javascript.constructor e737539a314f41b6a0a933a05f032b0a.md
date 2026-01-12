# constructor e737539a314f41b6a0a933a05f032b0a

Owner: Edwin

# constructor

Owner: edwin S

## function

```jsx
function Person(first, last, age, eye) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
}
```

---

## Class

```jsx
class Person {
    constructor() {
        this.name = "edwin";
        this.age = 100;
    }
}
```

---

## Type checking

```jsx
(2).constructor === Number;                 // true
(true).constructor === Boolean;             // true
('str').constructor === String;             // true
([]).constructor === Array;                 // true
(function() {}).constructor === Function;   // true
({}).constructor === Object;                // true
```