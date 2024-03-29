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

Variable assignment vs defining methods... Are variable assignments really a sort of memoization? Which syntax is better?

```ruby
class Foo
	def compute
		some_value = calculate_value

		do_something(some_value)
		do_something_else(some_value)
	end

	def calculate_value
		...
	end

	...
end
```

```ruby
class Foo
	def compute
		do_something(some_value)
		do_something_else(some_value)
	end

	def some_value
		@some_value ||= calculate_value
	end
end
```

The second one seems best when `calculate_value` is based on inputs that don't change.
TODO compare/contrast when values are computed... when would you want to recompute a value?

Singleton classes

Class vs super

forwarding arguments (positional, keyword, block)... when does super automatically forward them?
Is ... a thing? How does single star forwarding work in 3.2 (if it does)?

Is it an error to call a function without a block but which has a format argument of &blk? If you have a Proc object, do you have to precede it by an ampersand for it to be used as the function's block? Show an example of passing it both as a positional parameter AND as the block.

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

Enumerable
String
Array
Hash
Proc


Tricks
- How to find where a method is coming from: puts obj.method(:method_name).owner. Also class. See what happens if it's a module method, singleton_class method.
- Use Object#send to bypass visibility checks (use sparingly, useful for unit testing)

Deconstructing pairs (and others) into block arguments.

```ruby
# TODO is there a better way to do: .each { |job| yield job } YES... here's an example of forwarding to another each:  

class Foo  
  def each(&blk) # note: you can't capture the block with the split operator, e.g. `*args`. You need to use &.  
    (1..5).each(&blk)  
  end  
end  
  
f = Foo.new  
 
f.each { |i| puts i }  
  
def after(this)  
  this.call  
  yield  
end  

say_hello = proc { puts "Hello!" }  
say_hi = lambda { puts "Hi!" }  

# TODO understand difference between Proc and lambda.  I know the return behavior is one thing.  

after(say_hello) { puts "Goodbye!" }  
after(say_hi) { puts "Bye!" }  

# Not a syntax error if method expects to capture the block but none given... just becomes nil

def with(&blk)  
  if blk then blk.call else puts("No block given") end  
end  
  
with { puts "A block WAS given" }  
with
```

When setting an instance variable, that has accessors, you need to use self:

```ruby
class Person
  attr_accessor :name

  def set_name(new_name)
    self.name = new_name # Correct way to set the value of the instance variable
    # name = new_name    # Incorrect way, creates a new local variable
  end
end

person = Person.new
person.set_name("John")
puts person.name #=> "John"
```



---
References:

