## Boxing

Boxing is the process of converting a primitive type to its corresponding wrapper class.

 
```java
Integer boxedInt = Integer.valueOf(15);
Integer boxedInt = new Integer(15);
```

---

## Auto-boxing

```java
Integer boxedInt = 15;
```

---

## Unboxing

Unboxing is the process of extracting the primitive value from a wrapper class.

```java
Integer boxedInteger = 15;
int unboxedInt = boxedInteger.intValue();
```
