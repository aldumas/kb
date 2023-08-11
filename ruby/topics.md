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

---
References:

