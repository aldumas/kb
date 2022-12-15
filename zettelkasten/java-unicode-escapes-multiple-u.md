---
created-at: 2022-12-15 13:19
role: idea
tags: 
---

# Any number of u's are allowed in an escape

To help tools process unicode [[java-char-escapes|escapes]] back and forth in program text, any number of u's are allowed in the escape, e.g. `\u000a == \uuuuuuu000a`. This allows the tools to reverse conversions and get the exact source code back prior to the conversion.

---
# References

[[Core Java - Volume 1#03 - Fundamental Programming Structures in Java]]
[[Core Java - 03.03.03b.pdf]]