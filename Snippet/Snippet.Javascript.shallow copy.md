# shallow copy

Owner: Edwin

- A shallow copy of an object creates a new object, but it does not create copies of nested objects within the original object.
- Instead, it copies references to the nested objects. This means that changes made to the nested objects in the copied structure will also affect the original structure, and vice versa.
- Shallow copy methods are usually quicker and require less memory because they don't duplicate the entire structure.

- [Object.assign](https://www.notion.so/dc4c4426d90e4b75a518e8810079360b?pvs=21)
- [Spread Operator](Expressions%20&%20Operators%20c41aee8127bb4923ade37bc965b7c7b6/spread%20operator%20684517c59eb74b4988c8e117d05daac5.md)