# call

Owner: Edwin

```jsx
function Product(name, price) {
  this.name = name;
  this.price = price;
}

function Food(name, price) {

  //Product constructor is called
  // This allows the Food object to inherit the name and price properties from the Product object.
  Product.call(this, name, price);
  this.category = "food";
}

console.log(new Food("cheese", 5).name); // cheese
```