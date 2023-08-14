---
created-at: 2023-08-13 20:58
tags: ruby
---

The `Kernel` modules contains some functions which convert their arguments.

1. `Array`
2. `Complex`
3. `Float`
4. `Hash`
5. `Integer`
6. `Rational`
7. `String`

Using these functions allows for more flexible code. The upshot is that these functions check for certain conditions and based on those conditions will invoke an appropriate method on the object to actually perform the conversion. For example, `Array` will call `to_ary` on the object if it exists, otherwise it will call `to_a`. By using `Array` instead of directly calling `to_a` to perform the conversion, you allow your code to receive objects which have a `to_ary` method instead of `to_a` or have both but which defines `to_ary` to return a customized form of the result.

Other functions may raise errors (and possibly allow you to suppress them) based on some conditions.

For `Array`, `Integer`, and `String`, another way to view these functions is that they try to do an implicit conversion first using one of the implicit conversion methods: `to_ary`, `to_int`, or `to_str` and then if that's not available falls back to one of the explicit conversion methods: `to_a`, `to_i`, `to_s`. This does not hold for `Complex`, `Float`, `Hash`, or `Rational` however.

---
References:

