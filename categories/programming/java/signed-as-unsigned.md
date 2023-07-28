---
created-at: 2022-12-14 12:21
role: idea
tags: java primitives
---

Due to the nature of binary arithmetic, the following operations can be performed on signed integers as if they were unsigned:

- addition
- subtraction
- multiplication

The `Integer` and `Long` classes have methods to perform unsigned division.

For other operations, call `Byte.toUnsignedInt(b)` to get an int value between 0 and 127, perform the calculations, then cast it back to a `byte`.

---
# References

[[Core Java - Volume 1#03 - Fundamental Programming Structures in Java]]
[[Core Java - 03.03.01b-03.03.02a.pdf]]