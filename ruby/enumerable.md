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



When would you use this?
- [`Object#to_enum`](dfile:///Users/dumas/Library/Application%20Support/Dash/DocSets/Ruby_3/Ruby.docset/Contents/Resources/Documents/Object.html#method-i-to_enum)
    
- [`Object#enum_for`](dfile:///Users/dumas/Library/Application%20Support/Dash/DocSets/Ruby_3/Ruby.docset/Contents/Resources/Documents/Object.html#method-i-enum_for)
    
- [`Enumerator.new`](dfile:///Users/dumas/Library/Application%20Support/Dash/DocSets/Ruby_3/Ruby.docset/Contents/Resources/Documents/Enumerator.html#method-c-new)

---
References:

