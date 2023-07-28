---
created-at: 2022-12-14 12:04
role: idea
tags: java primitives
---

# Floating point literals
Without a suffix, a number in fixed point or exponential form will be typed as a `double`. If you want the literal to be typed as a `float`, you can use a `F` or `f` suffix, e.g. `3.14f`.

If you want to be explicit about the fact that a number is a `double`, you can supply a `D` or `d` suffix, e.g. `3.14d`. This is mostly useful if you want to have a double literal that would normally be interpreted by the compiler as an integer literal, e.g. `42d`. In this case, however, it might be clearer to write the literal as `42.` or `42.0`.

## Exponential form
Exponential form literals use `E` or `e` to denote the decimal exponent, e.g. `2.99792458e8` is 2.99792458 x 10^8.

## Hexadecimal floating point literals
Floating point literals can also be written in hexadecimal using exponential form, though the exponent is still in base-10, e.g. 2^-3 can be written as `0x1.0p-3`. Note that instead of `E` or `e` before the exponent, we use `P` or `p` since `E`  and `e` is a hexadecimal digit. Also note that the base of the exponent is 2.

**Therefore, hexadecimal floating point literals are a mixture of base-16, base-2, and base-10.**

>> [!example]
>> 40.25 can be represented as `0xa.1p2`. This is the same as (10 \* 16^0 + 1 \* 16^-1) \* 2^2.

---
# References

[[Core Java - Volume 1#03 - Fundamental Programming Structures in Java]]
[[Core Java - 03.03.01b-03.03.02a.pdf]]
[[Core Java - 03.03.02b-03.03.03a.pdf]]
