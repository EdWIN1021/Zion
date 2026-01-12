# Generics



## Type Parameters

A type parameter is a generic class. or generic method's declaration of the type.

You can bind a type parameter with the use of the extends keyword, to specify an upper bound.


Generic Class

```java
public class Team<T> {}
```

Generic Method

```java
public <T> void doSomething(T t){}
```

---

## Type Arguments

A type argument declares the type to be used, and is specified in a type reference:
- A local variable reference
- Method parameter declaration
- field declaration

```java
Team<BaseballPlayer> team = new Team<>();
```

A wildcard can only be used in a type argument, not in the type parameter declaration
- A wildcard is represented with the ? character
- A wildcard means the type is unknown

```java
List<?> unknownList;
```


==You cannot specify both an upper bound and a lower bound, in the same declaration==

| Argument | Example |
|---|---|
| unbounded | `List<?>` |
| upper bound | `List<? extends Student>` |
| lower bound |`List<? super LPAStudent>`|
