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

implicit conversion - when does it happen? https://docs.ruby-lang.org/en/master/implicit_conversion_rdoc.html It seems like it's just that the callee expects a certain method that has no input and a restricted output. What is the distinction with explicit conversions? Is it that the caller does explicit conversions while the callee does the implicit ones? It seems like this works with those Kernel methods, e.g. to create an Array using functions which test for to_ary first and to_a second. Those functions tend to try "implicit conversion" first and then "explicit conversion". implicit conversions and x-convertible objects. sounds like implicit conversions are used when working with system functions or libraries. https://github.com/rails/rails/commit/188cc90af9b29d5520564af7bd7bbcdc647953ca. Confident Ruby also talks about explicit conversions being where the target class is unrelated to the source class, whereas implicit conversions are where they are closely related. https://marcgg.com/blog/2017/01/23/ruby-to-s-to-str/. It sounds like some operations want to enforce that the thing they are working with is not just representable as a string but is essentially a string. `to_str` needs to be considered a CONVERSION of the thing to a string, whereas `to_s` is just a view which could be for any number of purposes (e.g. a message to the user, a message to the developer, marshalling for sending the object to another system, etc.) So, the question is: Do I just want SOME string representation of this object, or do I want this object AS a string?

implicit vs explicit conversion methods, e.g. to_s vs to_str, to_i vs to_int, etc. Checking presence of implicit conversion methods for duck typing???

gauging code - how well does it express the idea?

How can you set self for code that runs in a passed-in block? E.g. execute { a_method }, how to set self for the self.a_method call.

Recipes:
- Creation
	- Create an array of n objects


Why use each_with_object instead of just using a closure?

Struct
- each_pair


Tricks
- How to find where a method is coming from: puts obj.method(:method_name).owner. Also class. See what happens if it's a module method, singleton_class method.

---
References:

