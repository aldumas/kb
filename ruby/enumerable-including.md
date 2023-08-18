---
created-at: 2023-08-18 11:44
tags: ruby, todo
---

To enable your own class to support all the `Enumerable` methods, you need to:
1. include the `Enumerable` module in your class
2. define an `each` method which returns successive elements of the collection

```ruby
class Rhyme
	include Enumerable

	def each
		yield "Eenie meenie minie moe"
		yield "Catch a tiger by his toe"
		yield "If he hollers, let him go"
		yield "Eenie meenie minie moe"
	end
end

lines = Rhyme.new

# By defining `each`, we have access to other `Enumerable` methods because they are defined in terms of `each`, e.g. `map`

puts lines.map { |line| line.split.last } # => ["moe", "toe", "go", "moe"]
```

Here's another example:

```ruby
class Multiples  
  include Enumerable  
  
  def each(&blk)  
    (@num...@max).step(@num).each(&blk)  
  end  
  
  def initialize(num, max)  
    @num = num  
    @max = max  
  end  
end  
  
class Integer  
  def perfect_square?  
    Math.sqrt(self) % 1 == 0  
  end  
end  
  
multiples_of_3 = Multiples.new(3, 10)  
  
# We can call any? because we included Enumerable and defined an each method

puts multiples_of_3.any?(&:perfect_square?)
```


TODO add support to call each without a block.. How do we get it to return an enumerator?



---
References: