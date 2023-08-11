---
created-at: 2022-12-14 23:14
role: idea
tags: java primitives
---

# Positive and negative infinity
There are special values of floating point numbers which correspond to positive and negative infinity. E.g. `1/0` will produce positive infinity.

Be aware of the [[integer-floating-point-division-by-zero-difference|difference between floating point and integer division by zero]].

These values are available at `Double.POSITIVE_INFINITY` and `Double.NEGATIVE_INFINITY`, though they are never used in practice.

There's one more special value, which represents the concept of [[floating-point-nan|Not a Number]].

---
# References

[[Core Java - Volume 1#03 - Fundamental Programming Structures in Java]]
[[Core Java - 03.03.02b-03.03.03a.pdf]]