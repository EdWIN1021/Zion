# bind

Owner: Edwin

```jsx
const ac_passenger = {
  airline: "Air Canada",
  iataCode: "AC",
  book(name, flightNum) {
    console.log(
      `${name} booked a seat on ${this.airline} flight ${this.iataCode}${flightNum}`
    );
  },
};

const aa_passenger = {
  airline: "American Airlines",
  iataCode: "AA",
};

//bind 返回一个方法需要被调用
ac_passenger.book.bind(aa_passenger)("EDWIN", 456);
```