---
created-at: 2022-12-14 12:37
role: idea
tags: java primitives
---

# Floating point types

| Type   | Storage requirements | Range                                   | # Significant figures |
| ------ | -------------------- | --------------------------------------- | --------------------- |
| float  | 4 bytes              | Approx +/- 3.40282347 x 10^38           | 6-7                   |
| double | 8 bytes              | Approx +/- 1.79769313486231570 x 10^308 | 15                    | 

#advice Use `double` unless you have a specific reason to use `float`, like if you are working with a library that uses them, or you need to store a lot of floating point values and don't need the extra precision.

Also read about [[java-floating-point-literals|floating point literals]].

Be aware that [[java-floating-point-math-different-results|floating point math might not produce the same results]] across machines.

#advice For calculations which require exact results without floating point roundoff, use `BigDecimal`.

---
# References

[[Core Java - Volume 1#03 - Fundamental Programming Structures in Java]]
[[Core Java - 03.03.01b-03.03.02a.pdf]]
[[Core Java - 03.03.02b-03.03.03a.pdf]]