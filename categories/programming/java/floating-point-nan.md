---
created-at: 2022-12-14 23:21
role: idea
tags: java primitives
---

# Not a number
Some calculations may produce a value which represents a result of an invalid calculation. E.g. `0/0` or `Math.sqrt(-1)`.

This value is available at `Double.NaN`, though it is never used in practice.

>[!caution]
>`NaN` values are all distinct; that is, for any variable `x` which holds the special `NaN` value, `x == Double.NaN` will never be true. To check for this value, use `Double.isNaN(x)`.

There are two other special floating point values which represent the concept of [[floating-point-infinity|infinity]].

---
# References

[[Core Java - Volume 1#03 - Fundamental Programming Structures in Java]]
[[Core Java - 03.03.02b-03.03.03a.pdf]]