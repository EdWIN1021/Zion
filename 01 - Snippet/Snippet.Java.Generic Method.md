# Generic Methods

- For a method, type parameters are placed after any modifiers and before the method's return type.

- The type parameter can be referenced in method parameters:
	- method return type 
	- in the method code block
	- class's type parameter 
- Can be used for collections with type arguments
- Can be used for static methods on generic class
- Can be used on non-generic class
- The generic method type parameter is separate from a generic class type parameter

```java
public <T> String myMethod(T input){
	return input.toString();
}

```

