---
created-at: 2022-12-14 23:44
role: idea
tags: 
---

# `char` type
A `char` is a 2 byte value which represents a unicode code unit (not a [[java-code-point|code point]]) in the UTF-16 encoding. It can hold any value between `0x0000` and `0xffff`.

Since many characters require 2 code units to encode, you cannot rely on a single `char` to represent a character unless you know you are not dealing with characters which require 2 code units.

`char` literals are surrounded by single quotes, e.g. `'a'`.

>> [!caution] Do not confuse literal characters with literal strings
>> If you surround the character with double quotes, you get a single character `string`, not a `char`.

`char`s can be converted to and from integral values, e.g. `'a' + 1 == 'b'`.

---
# References

[[Core Java - Volume 1#03 - Fundamental Programming Structures in Java]]
[[Core Java - 03.03.02b-03.03.03a.pdf]]