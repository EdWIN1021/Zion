# Function Interface

The function interface is the framework that lets a lambda expression be used.

| Interface Category | Basic Method Signature | 
| -------------------| -----------------------|
| Consumer           | `void accept(T t)`       |
| BiConsumer         | `void accept(T t, U u)`  |
| Function           | `R apply(T t)`          |
| Predicate          | `boolean test(T t)`      |
| Supplier           | `T get()`               |
| `Function<T, R>`     | `R apply(T t)`           |
| `BiFunction<T, U, R>` | `R apply(T t, U u)`      |
| `UnaryOperator<T>` | `T apply(T t)`           |
| `BinaryOperator<T>`   | `T apply(T t1, T t2)`      |

---

## Convenience Methods 

| Interface Category | method | 
| -------------------| --------------------------|
| Function           | `function1.andThen(function2)`|
| Function           | `function2.compose(function1)`|
| Consumer           | `consumer1.andThen(consumer2)`|
| Predicate          | `predicate1.and(predicate2)`  |
| Predicate          | `predicate1.or(predicate2)`   |
| Predicate          | `predicate1.negate()`       |

---

## Comparator's additional helper methods
| Type of Method | method Signature | 
| ---------------| -----------------|
| static | Comparator comparing(Function keyExtractor) |
| static | Comparator naturalOder() |
| static | Comparator reverseOder() |
| default | Comparator thenComparing(Comparator other) |
| default | Comparator thenComparing(Function keyExtractor) |
| default | Comparator reverse() |





