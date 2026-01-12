# Getter and Setter 0687b578709e44ed9601997de0d507a0

Owner: Edwin

Owner: edwin S

---

```jsx
var person = {
  firstName: "Yang",
  lastName : "Shi",
  language : "english",

  fullName : function() {                        //this is a property
    return this.firstName + " " + this.lastName;
  },

  get fullName() {                              //this is a function
    return this.firstName + " " + this.lastName;
  },

  get getLanguage() {        //language getter
    return this.language;
  },

  set setLanguage(newLanguage) {        //language Setter
    return this.language = newLanguage;
  },
};

console.log(person.getLanguage);

/*
  output:
    english
*/
```