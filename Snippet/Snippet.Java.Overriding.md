## Overriding

- Method overriding, means defining a method in a child class, that already exist in the parent class, with the same signature.
- Method overriding is also known as Runtime Polymorphism or Dynamic Method Dispatch, because the method that is going to be called, is decided at runtime, by the JVM.

---
- Must have the same parameters and same name.
- Must have the same return type or covariant return type.
- Must NOT have a lower modifier but may have a higher modifier.
- Must NOT throw a new or broader checked exception. 