---
created-at: 2022-12-12 23:28
role: idea
tags: java primitives
---

All 4 integral primitives are signed (even `byte`).

| Type  | Storage requirements | Range                                                   |
| ----- | -------------------- | ------------------------------------------------------- |
| byte  | 1 byte               | -128 to 127                                             |
| short | 2 bytes              | -32,768 to 32,767                                       |
| int   | 4 bytes              | -2,147,483,648 to 2,147,483,647                         |
| long  | 8 bytes              | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 |

These sizes and ranges are fixed by the language spec and are therefore not machine-dependent.

#advice Use int unless you have a specific reason to use one of the others.

Though these types are all signed, it is possible to [[java-signed-as-unsigned|work with them as unsigned]].

Also read about integer [[java-literals|literals]].

---
# References

[[Core Java - Volume 1#03 - Fundamental Programming Structures in Java]]
[[Core Java - 03.01-03.03.01a.pdf]]
[[Core Java - 03.03.01b-03.03.02a.pdf]]