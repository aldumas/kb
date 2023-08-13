---
created-at: 2023-08-13 15:06
tags: ruby
---

Variables that spring into existence in a branch of a control structure are accessible after the control structure completes, even if a branch is taken which does not initialize the variable. In this case, the value will be `nil`, but the variable will still be defined and will not cause a `NameError`. 

```ruby
class Foo
	# puts var # => NameError: undefined local variable or method `var' 
	 
	def a_method  
		if false  
			var = 42 # var is defined from this point on, even though execution doesn't reach here  
		end  
  
		puts var.inspect # => "nil"  
	end  
end  
  
Foo.new.a_method
```

---
References:

