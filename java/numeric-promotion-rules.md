---
created-at: 2022-12-13 08:45
role: idea
tags: implicit coercion conversion
---

# Numeric Promotion Rules

When numeric values of different types (including the [[char-type|char]] type) are combined with binary operators, the following automatic conversion rules go into effect, in this order:

1. If either operand is a [[floating-point-types|double]], the other operand is converted into a double.
2. If either operand is a [[ava-floating-point-types|float]], the other operand is converted to a float.
3. If either operand is a [[integral-types|long]], the other operand is converted to a long.
4. Otherwise, both operands will be converted to [[integral-types|int]].

The last item can cause surprising results if you are doing `byte` or `short` math. E.g. consider the following code:

```java
byte a = Byte.MAX_VALUE;
var b = a + 1;
```

The  type of `b` is `int`, not `byte`, and its value is `128`, not `-128` since the the math was done with `int`s and not `byte`s, so no overflow occurred.

There are other instances where Java will [[numeric-coercion|coerce numeric values]]. 

---
# References
