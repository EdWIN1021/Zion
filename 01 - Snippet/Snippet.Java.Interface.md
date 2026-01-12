# Interface

- We don not have to declare the interface type abstract, because this modifier is Implicitly declared, for all interfaces

- Interfaces can be extended, similar to classes, using the extends keyword
- An interface does not implements another interface

```java
interface OrbitEarth extends FlightEnabled {}
```

-  All members on an interface are implicitly public

- These all mean the same thing on an interface 

```java
// These all mean the same thing on an interface 

interface FlightEnabled {  
    public abstract void takeOff();  
    
    abstract void land();  
    
    void fly();  
}

```

- A field declared on an interface is always public, static and final

```java
// These all mean the same thing on an interface 

double MILES_TO_KM = 1.60934;
final double MILES_TO_KM = 1.60934;
public final double MILES_TO_KM = 1.60934;
public static final double MILES_TO_KM = 1.60934;
```

- An interface is usually named, according to the set of behaviors it describes.

```java
public interface FlightEnabled {}
```


### Extension method

- An extension method is identified by the modifier default, so it's more commonly known as the default method
- This method is a concrete method, meaning it has a code block, and we can add statements to it.
- It has to have a method, even just an empty set of curly braces
- it's a lot like a method on a superclass, because we can override it