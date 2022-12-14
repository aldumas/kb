---
created-at: 2022-12-14 12:04
role: idea
tags: 
---

# Literals


## Floating point numbers
Without a suffix, a number in fixed point form or scientific notation will be typed as a `double`. If you want the literal to be typed as a `float`, you can use a `F` or `f` suffix, e.g. `3.14f`.

If you want to be explicit about the fact that a number is a double, you can supply a `D` or `d` suffix, e.g. `3.14d`. This is mostly useful if you want to have a double literal that would normally be interpreted by the compiler as an integer literal, e.g. `42d`. In this case, however, it might be clearer to write the literal as `42.` or `42.0`.

#todo binary fp literal



---
# References

[[Core Java - Volume 1#03 - Fundamental Programming Structures in Java]]
[[Core Java - 03.03.01b-03.03.02a.pdf]]
[[Core Java - 03.03.02b-03.03.03a.pdf]]
