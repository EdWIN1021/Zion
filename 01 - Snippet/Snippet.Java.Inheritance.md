## Inheritance

- Although a subclass includes all of the members of its superclass, it cannot access those members of the superclass that have been declared as private.
- When an overridden method is called through its subclass, it will always refer to the version of that method defined by the subclass.
- Method overriding occurs only when the names and the type signatures of the two methods are identical. If they are not, then the two methods are simply overloaded
- Inheritance defines an **IS A** relationship.
- A class can only extends a single class, which is why Java is called single inheritance.