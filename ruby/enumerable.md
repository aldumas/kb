---
created-at: 2023-08-17 19:18
tags: ruby todo
---

The `Enumerable` class provides methods for working with collections that can be iterated over. Some classes which include it are:

- Array
- Hash
- Struct
- Range
- Enumerator

Here are some commonly used methods in `Enumerable`:

- each
- map
- select (or filter)
- reject
- reduce (or inject)
- find (or detect)
- any?
- all?
- none?
- sort
- zip
- count



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
```


each_with_index
each_with_object (why use this instead of a closure?) Answer: to create an enumerator that includes it such that some other code can enumerate it.

```ruby
def print_pairs(pairs) # TODO how would you specify that the block passed to pairs.each should accept 2 args?
  pairs.each { |first, second| puts "#{first}: #{second}" }
end

fruit = %w(apple banana pear peach kiwi)

pairs = fruit.each_with_object(42)

print_pairs(pairs)
```



When would you use this?
- [`Object#to_enum`](dfile:///Users/dumas/Library/Application%20Support/Dash/DocSets/Ruby_3/Ruby.docset/Contents/Resources/Documents/Object.html#method-i-to_enum)
    
- [`Object#enum_for`](dfile:///Users/dumas/Library/Application%20Support/Dash/DocSets/Ruby_3/Ruby.docset/Contents/Resources/Documents/Object.html#method-i-enum_for)
    
- [`Enumerator.new`](dfile:///Users/dumas/Library/Application%20Support/Dash/DocSets/Ruby_3/Ruby.docset/Contents/Resources/Documents/Enumerator.html#method-c-new)

---
References:

