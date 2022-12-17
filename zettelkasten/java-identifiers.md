---
created-at: 2022-12-16 16:47
tags: java
---

Rules for identifiers:

1. Only letters, digits, currency symbols, and punctuation connectors (e.g. underscore) are allowed.
3. Must start with a letter or underscore.
4. A single underscore is not allowed.

The dollar sign currency symbol is technically allowed in identifiers but is reserved for compiler-generated names.

Letter and digit characters can be from any language. E.g. you can have an identifier named `π`.

These functions are helpful in determining whether a given character may be used in an identifier:

```java
Character.isJavaIdentifierStart(ch)
Character.isJavaIdentifierPart(ch)
```

---
References:

[[Core Java - Volume 1#03 - Fundamental Programming Structures in Java]]
[[Core Java - 03.03.04-03.04.01a.pdf]]