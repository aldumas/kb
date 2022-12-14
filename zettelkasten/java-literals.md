---
created-at: 2022-12-14 12:04
role: idea
tags: 
---

# Literals

## Integers
In source code, any integer without a suffix is typed as `int`. If the value falls outside the range that can be represented as an `int`, a compiler error will result.

A `long` can be represented by adding an `L` or `l` suffix after the integer, e.g. `42L`.

Underscores in integer literals are ignored by the compiler, e.g. `1_000`. This is just for readability.

### Prefixes for other number bases
Any integer without a prefix is interpreted as a decimal number. Java supports the following prefixes to specify numbers in other bases.

| Base             | Prefix   | Example  |
| ---------------- | -------- | -------- |
| 16 (hexadecimal) | 0x or 0X | 0x2a     | 
| 8 (octal)        | 0        | 042      |
| 2 (binary)       | 0b or 0B | 0b101010 |

## Floating point numbers
#todo


---
# References

[[Core Java - Volume 1#03 - Fundamental Programming Structures in Java]]
[[Core Java - 03.03.01b-03.03.02a.pdf]]