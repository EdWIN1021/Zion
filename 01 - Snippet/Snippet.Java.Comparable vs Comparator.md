# Comparable vs Comparator

| Comparable | Comparator |
|---|---|
|Compares the argument with the current instance| Compares two arguments of the same type with each other |
|Called from the instance of the class that implements Comparable| Called from an instance from Comparator|
|Best practice to have `this.compareTo(o) == 0` result in `this.equals(o)` being true| Does not require the class itself to implement Comparator, though you could also implements it this way |
|`Arrays.sort(T[]elements)` requires T to implement Comparable|`Array.sort(T[]elements, Comparator<T>)` does not require T to implement Comparable