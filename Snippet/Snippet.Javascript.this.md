# this

Owner: Edwin

<aside>
💡 The this keyword in JavaScript is a special keyword that refers to the current execution context or the object that is currently executing the code. Its value is determined by how a function is called, and it can behave differently depending on the context in which it is used.

</aside>

- **Global Context**
    - window or node object
- **Function Context**
- **Constructor Functions**
    - When a function is used as a constructor with the new keyword, this refers to the newly created object
- **Event Handlers**
- **Arrow Functions**

```jsx
"use strict";
const fun = function () {
  console.log(this);  // undefined
};

fun();
```

```jsx

const fun = function () {
  console.log(this);  // window / object
};

fun();
```

```jsx

const fun = () => {
  console.log(this);  //parent scope => window
};

fun();
```

```
const person = {
  firstName: "edwin",
  lastName: "shi",

  printFirstName: function () {
    console.log(this.firstName);

    const self = this;
    const printLastName = function () {
      console.log(self.lastName);
    };

    printLastName();
  },
};

person.printFirstName();
```

```jsx
const person = {
  firstName: "edwin",
  lastName: "shi",

  printFirstName: function () {
    console.log(this.firstName);

    const printLastName = () => {
      console.log(this.lastName);
    };

    printLastName();
  },
};

person.printFirstName();
```