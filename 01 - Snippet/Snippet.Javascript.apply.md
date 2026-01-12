# apply

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

ac_passenger.book.apply(aa_passenger, ["EDWIN", 456]);
```