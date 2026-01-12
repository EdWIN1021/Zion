# Getter and Setter

Owner: Edwin

---

```
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