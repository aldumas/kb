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

Note that String does NOT include `Enumerable`, but it does have some methods to iterate over the characters.

Here are some commonly used methods in `Enumerable`:

- [each/each_with_index/each_with_object](ruby/enumerable-each.md)
- map
- select (or filter)/reject
- reduce (or inject)
- find (or detect)/find_all
- any?
- all?
- none?
- sort/sort_by
- zip
- count

Other methods:

- chain
- chunk/chunk_while
- collect/collect_concat
- compact
- cycle
- drop/drop_while
- each_cons
- each_entry
- each_slice
- each_with_index
- each_with_object
- entries
- find_index
- filter_map
- first
- flat_map
- grep/grep_v
- group_by
- include?
- lazy
- min/min_by
- max/max_by
- member? (how is this different than include?)
- minmax/minmax_by
- one?
- partition
- reverse_each
- slice_after/slice_before/slice_when
- sum
- take/take_while
- tally
- to_a
- to_h
- to_set
- uniq





```


TODO do examples of enumerating over Array vs Hash vs Struct

When would you use this?
- [`Object#to_enum`](dfile:///Users/dumas/Library/Application%20Support/Dash/DocSets/Ruby_3/Ruby.docset/Contents/Resources/Documents/Object.html#method-i-to_enum)
    
- [`Object#enum_for`](dfile:///Users/dumas/Library/Application%20Support/Dash/DocSets/Ruby_3/Ruby.docset/Contents/Resources/Documents/Object.html#method-i-enum_for)
    
- [`Enumerator.new`](dfile:///Users/dumas/Library/Application%20Support/Dash/DocSets/Ruby_3/Ruby.docset/Contents/Resources/Documents/Enumerator.html#method-c-new)

---
References:

