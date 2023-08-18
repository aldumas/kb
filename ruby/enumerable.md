---
created-at: 2023-08-17 19:18
tags: ruby
---

The `Enumerable` class provides methods for working with collections that can be iterated over. Some classes which include it are:

- Array
- Hash
- Struct
- Range
- Enumerator



each_with_index
each_with_object (why use this instead of a closure?) Answer: to create an enumerator that includes it such that some other code can enumerate it.

```ruby
def print_pairs(pairs)
  pairs.each { |first, second| puts "#{first}: #{second}" }
end

fruit = %w(apple banana pear peach kiwi)

pairs = fruit.each_with_object(42)

print_pairs(pairs)
```


---
References:

