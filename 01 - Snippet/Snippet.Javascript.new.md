# new

Owner: Edwin

```jsx
function Person(name) {
  this.name = name;
}

const p1 = new Person("edwin");

p1.__proto__ === Person.prototype;

p1.constructor === Person; 

Person.prototype.constructor === Person
```

1. an empty object is created
2. this point to the empty object

 3. Points newInstance's [[Prototype]] to the constructor function's prototype property

![new%20fb7ffe82e17d42f0966c771437ba39e0/classnew%E4%B8%80%E4%B8%AA%E5%AF%B9%E8%B1%A1imageimage_DrhA7VeFWQ.png](new%20fb7ffe82e17d42f0966c771437ba39e0/classnew%E4%B8%80%E4%B8%AA%E5%AF%B9%E8%B1%A1imageimage_DrhA7VeFWQ.png)

1. The new object is returned by constructor function