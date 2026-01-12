# Object

Owner: Edwin

### **Object Literal**

```jsx
var myObject = {
  key1: 'value1',
  key2: 'value2'
};
```

### **Object Constructor**

```jsx
var myObject = new Object();
myObject.key1 = 'value1';
myObject.key2 = 'value2';
```

### **Object.create()**

```jsx
var myObject = Object.create(somePrototype);
```

### **Function Constructor**

```jsx
function MyObject(key1, key2) {
  this.key1 = key1;
  this.key2 = key2;
}

var myObject = new MyObject('value1', 'value2');
```

### **Class Syntax**

```jsx
class MyObject {
  constructor(key1, key2) {
    this.key1 = key1;
    this.key2 = key2;
  }
}

var myObject = new MyObject('value1', 'value2');
```