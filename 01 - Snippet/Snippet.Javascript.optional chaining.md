# optional chaining

Owner: Edwin

```
const adventurer = {
  name: "Alice",
  cat: {
    name: "Dinah",
  },
};

const str = adventurer.cat?.name;
// str => Alice

 const str = adventurer.cat?.age;
// str => undifined
```