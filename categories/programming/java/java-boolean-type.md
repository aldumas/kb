---
created-at: 2022-12-15 23:34
role: idea
tags: java primitives
---

# Boolean

This type only accepts 2 values: `true` or `false`.

You cannot cast to an integral type. This is to avoid bugs in conditionals. If you need to convert a boolean to a 1 or a 0, you can do this:

```java
var boolAsInt = someBoolean ? 1 : 0;
```

---
# References

[[Core Java - Volume 1#03 - Fundamental Programming Structures in Java]]
[[Core Java - 03.03.04-03.04.01a.pdf]]