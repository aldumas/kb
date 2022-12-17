---
created-at: 2022-12-16 09:19
tags: java
---

Before you can use a variable, you must declare and [[java-initialization|initialize]] it.

To declare a variable, you list the type and variable name. E.g.

```java
int age;
```

You can also use the [[java-keyword-var|var keyword]] to declare the variable if you initialize it in the same statement.

Java supports [[java-multiple-declarations|multiple declarations]] in a single statement.

You can declare a local variable anywhere in a method (not just the beginning of a block), but it is best practice to declare it nearest where it is used, and preferably not until a useful initialization value is available.

In some languages, there's a distinction between declarations and definitions (the point where memory is set aside for the variable). Java does not have this distinction.

---
References:

[[Core Java - Volume 1#03 - Fundamental Programming Structures in Java]]
[[Core Java - 03.04.01b-03.04.04.pdf]]
[[Core Java - 03.04.01b-03.04.04.pdf]]