---
created-at: 2022-12-15 00:00
role: idea
tags: java unicode escapes
---

# Character escapes
Java supports the following escapes:

| Escape     | Meaning                                                     | Where applicable                           |
| ---------- | ----------------------------------------------------------- | ------------------------------------------ |
| `\b`       | backspace                                                   | `string` or `char` literals or text blocks |
| `\t`       | tab                                                         | `string` or `char` literals or text blocks |
| `\n`       | newline                                                     | `string` or `char` literals or text blocks |
| `\r`       | carriage return                                             | `string` or `char` literals or text blocks |
| `\f`       | line feed                                                   | `string` or `char` literals or text blocks |
| `\"`       | double quote                                                | `string` or `char` literals or text blocks |
| `\'`       | single quote                                                | `string` or `char` literals or text blocks |
| `\\`       | backslash                                                   | `string` or `char` literals or text blocks |
| `\s`       | space (preserve trailing space)                             | text blocks                                |
| `\newline` | newline (skip newline)                                      | text blocks                                |
| `\uXXXX`   | [[unicode-escapes-before-compilation|unicode escape]] | anywhere in program text                   |


---
# References

[[Core Java - Volume 1#03 - Fundamental Programming Structures in Java]]
[[Core Java - 03.03.02b-03.03.03a.pdf]]