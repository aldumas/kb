---
created-at: 2022-12-15 22:30
role: idea
tags: unicode
---

# Unicode surrogates

A range of code points within the [[code-planes|Basic Multilingual Plane]] do not correspond to any characters but are reserved for use in encoding Supplementary Characters by combining multiple code units. This range is referred to the Surrogate range/area and is divided into 2 subranges -- the high and low surrogate range.

High surrogate range: U+D800 - U+DBFF
Low surrogate range: U+DC00 - U+DFFF

In UTF-16, two code points are used to encode each Supplementary Character. The high 10 bits of the 20-bit offset above U+FFFF are encoded using values from the High surrogate range. Likewise, the low 10 bits of the 20-bit offset are encoded using values from the Low surrogate range.

See [Wikipedia UTF-16](https://en.wikipedia.org/wiki/UTF-16).

One of the benefits of this scheme is that, given a code unit, you can immediately tell if it is for a character, or whether it is part of encoding a Supplementary Character. It is also easy to determine which part of the Supplementary Character it is (the first or second code unit).

---
# References

[[Core Java - Volume 1#03 - Fundamental Programming Structures in Java]]
[[Core Java - 03.03.04-03.04.01a.pdf]]