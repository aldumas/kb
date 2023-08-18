---
created-at: 2023-08-18 11:44
tags: ruby
---

To enable your own class to support all the `Enumerable` methods, you need to:
1. include the `Enumerable` module in your class
2. define an `each` method

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


---
References:

