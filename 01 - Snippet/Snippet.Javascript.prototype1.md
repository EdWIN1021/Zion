# prototype

Owner: Edwin

- All Objects inherit properties and methods from prototype
- Object.prototype is on the top of the prototype inheritance chain
- Prototype property allows add new properties and method to constructors
- Function object has .__proto__ and .prototype properties
    - .__proto__ points to the Function.prototype object
    - .prototype used when you want to create objects using that function as a constructor
- object created by object literal does not have .prototype property, it has .__proto__