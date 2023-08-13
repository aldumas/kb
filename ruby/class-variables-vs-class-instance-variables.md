---
created-at: 2023-08-12 23:45
tags: ruby
---

There are two different types of variables that are associated with classes rather than instances of those classes.

```ruby
class Foo
	@class_instance_variable = 1
	@@class_variable = 2

	# You can access class instance variables from class methods
	def self.output_class_instance_variable_from_class_method
		puts @class_instance_variable
	end

	# You CANNOT access class instance variables from instance methods
	def output_class_instance_variable_from_instance_method
		# puts @class_instance_variable # => nil because it's not found
		raise "ERROR"
	end

	# You can access class variables from class methods
	def self.output_class_variable_from_class_method
		puts @@class_variable
	end

	# You can access class variables from instance methods
	def output_class_variable_from_instance_method
		puts @@class_variable
	end
end

Foo.output_class_instance_variable_from_class_method # => 1
Foo.output_class_variable_from_class_method # => 2

f = Foo.new
f.output_class_variable_from_instance_method # => 2
```

Class variables are shared between a class and all subclasses, whereas class instance variables are associated with just the one class (actually the singleton class of the class object).

>[!Advice]
>Class instance variables are preferred over class variables.

See https://www.ruby-lang.org/en/documentation/faq/8/#:~:text=What%20is%20the%20difference%20between,belong%20to%20one%20specific%20class.

---
References:

