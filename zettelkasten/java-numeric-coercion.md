---
created-at: 2022-12-13 09:06
role: idea
tags: implicit coercion conversion
---

Java will implicitly convert (coerce) numeric values in the following instances. Note that these coercions *will only take place if there is no loss of information*. In cases where there is a potential loss of information, you will need to perform an explicit [[java-casting|cast]].

1. When values of different types are [[java-numeric-promotion-rules|combined in an expression]] containing a binary operator.
2. When passed as a parameter to a method call where the parameter is defined as a different type. #todo 
3. When returned from a method defined with a different return type. #todo
4. #todo

#question What happens if I have the following cases: 1. method A receives int and method B (same name) received short, but I pass a short. Does the short version get called? Or does the compiler reject the program? What if I pass a byte, instead? In this last case, the short version got called. #todo see if this is officially defined in the spec.

---
# References
