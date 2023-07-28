---
created-at: 2022-11-30 12:49
role: idea
tags: java primitives advice
---

Treat strings as abstract data types and avoid working directly with `char`s. If you really need to work with the individual characters in the string, work with code points. Java `char`s are code units and might not represent the full character.

> [!quote]
> I strongly recommend against using the `char` type in your programs unless you are actually manipulating UTF-16 code units. You are almost always better off treating strings as abstract data types -- See Section 3.6, "Strings", on p. 61.


---
# References

[[Core Java - Volume 1#03 - Fundamental Programming Structures in Java]] § 3.3.4, p. 46