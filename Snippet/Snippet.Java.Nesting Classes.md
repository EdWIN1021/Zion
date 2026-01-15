# Nesting Classes

A class can contain other types with in the class body, such as other classes, interfaces, enums and records.

|Type|Desciption|
|---|---|
|static nested class|declared in class body. Much like a static field, access to this class is through the Class name identifier|
|instance or inner class|declared in class body. This type of class can only be accessed through an instance of the outer class.|
|local class|declared within a method body|
|anonymous class|unnamed class, declared and instantiated in same statement|

---

## Static Nested Class

The static nested class is a class enclosed in the structure of another class, declared as static

This means the class, if accessed externally, requires the outer class name as part of the qualifying name

This class has the advantage of being able to access private attributes on the outer class

The enclosing class can access any attributes on the static nested class, also including private attributes

---

## Inner Classes

Inner classes are non-static classes, declared on an enclosing class, at the member level.

Inner classes can have any of the four valid access modifiers

An inner class has access to instance members, including private members, of the enclosing class

---

## Local Classes

local classes are inner classes, but declared directly in a code block, usually a method body.

Because of that they don't have access modifiers, and are only accessible to that method body while it's executing

Like an inner class, they have access to all fields and methods on the enclosing class

They can also access local variables and methods arguments, that are final or effectively final

---

## Anonymous Classes

An anonymous class is a local class that doesn't have a name

The anonymous class is never created with a class declaration, but it's always instantiated as part of an expression

