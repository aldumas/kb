---
created-at: 2023-08-11 12:06
tags: ruby
---

truthiness

converting to boolean

type conversions. designing methods to do this so callers can pass in a wider range of types.

if else vs messages. hidden type checks.

Equality and impact on data structures

Rails - scopes and where chained with find_or_create_by includes the previous conditions (at least if the relation has not executed)

Rails - reusing relations as long as they have not executed (ok if relations created from them execute, just as long as they don’t). how could not keeping track of which have executed get you in trouble?

Lazy evaluation (does Ruby have something like Kotlin sequences?

Idioms

Variable assignment vs defining methods

Singleton classes

Class vs super

value || raise does not work syntactically, but you can wrap the raise in a method and call the method: value || raise_error_method

C code

memoization ||= vs ||= lambda {...}.call

implicit conversion - when does it happen? https://docs.ruby-lang.org/en/master/implicit_conversion_rdoc.html It seems like it's just that the callee expects a certain method that has no input and a restricted output. What is the distinction with explicit conversions? Is it that the caller does explicit conversions while the callee does the implicit ones? It seems like this works with those Kernel methods, e.g. to create an Array using functions which test for to_ary first and to_a second. Those functions tend to try "implicit conversion" first and then "explicit conversion". implicit conversions and x-convertible objects. sounds like implicit conversions are used when working with system functions or 

implicit vs explicit conversion methods, e.g. to_s vs to_str, to_i vs to_int, etc. Checking presence of implicit conversion methods for duck typing???

guaging code - how well does it express the idea?

---
References:

