# constructor

Owner: Edwin

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