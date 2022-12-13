---
created-at: 2022-12-13 09:06
role: idea
tags: coercion conversion
---

Java will implicitly convert (coerce) numeric values in the following instances:

1. When values of different types are [[java-numeric-promotion-rules|combined in an expression]] containing a binary operator.
2. When passed as a parameter to a method call where the parameter is defined as a different type. #todo 

#question What happens if I have the following cases: 1. method A receives int and method B (same name) received short, but I pass a short. Does the short version get called? Or does the compiler reject the program? What if I pass a byte, instead?

---
# References
