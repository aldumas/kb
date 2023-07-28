---
created-at: 2022-12-16 09:15
tags: java
---

You initialize a variable by providing it a value. This value can come from a literal, another variable, method call, new object construction, assignment expression, etc.

```java
int x = 42;
```

Initialization does not have to happen at declaration time.

```java
int x;
// ... code ...
x = 42;
```

#advice Try to keep the declaration and initialization as close as possible. Combining declaration and initialization in a single statement is ideal if it's possible.

It is a compile-time error to attempt to use a local variable without initializing it first.

```java
int x;
System.out.println(x); // ERROR
```

The compiler automatically initializes fields of objects and array elements to [[java-default-initialization|default values]], so it is not an error to use one of these without explicitly initializing it (but not recommended).

Arrays have a special [[java-initialization-arrays|initialization]] syntax.

When combining declaration and initialization in a single statement, you can use the [[java-keyword-var|var keyword]].

---
References:

[[Core Java - Volume 1#03 - Fundamental Programming Structures in Java]]
[[Core Java - 03.04.01b-03.04.04.pdf]]
