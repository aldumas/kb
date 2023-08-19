---
created-at: 2023-08-18 11:53
tags: ruby
---

Methods of [Enumerable](ruby/enumerable.md)
# each

## Ordering

The general concept of `each` does not suppose any particular order.

For Arrays, the order is the order of the elements in the array, but for Hash the order is not defined.

Let's say you have a Hash containing email addresses mapped to Users:

```ruby
User = Struct.new(:name, :birthdate, :)
	

emails_to_users = {}
```



When writing functions which call `each` on other objects to iterate over them, if the operation you are doing requires a specific order, you can either require the objects to define their `each` so that the ordering is inherit, or require them to provide a way for you to specify the ordering you desire from each. E.g. instead of calling `each` directly on the object passed in via an argument, send it a message to return you an iterator that iterates over the desired order. #todo think more on this.

#todo see Comparable


# each_with_index

# each_with_object

This method allows you to seed the `Enumerator` with an object that will be passed as the second argument into the block in addition to the value.

## Why use `each_with_object` instead of using a closure?

In many cases, instead of using `each_with_object`, you can just use `each` and let the block reference a variable in its parent scope:

```ruby
def print_color_preferences(name, colors)
	colors.each { |color| puts "#{name} likes #{color}" }
end

colors = %w(blue red orange yellow green)

print_color_preferences("Adam", colors)
```

You could also do it with `each_with_object` like this, where the difference is that the block receives `name` as an argument instead of pulling it from its parent scope:

```ruby
def print_color_preferences(name, colors)
	colors.each_with_object(name) { |color, name| puts "#{name} likes #{color}" }
end

colors = %w(blue red orange yellow green)

print_color_preferences("Adam", colors)
```

One benefit to doing it this way is that the dependencies of the block are explicit. It depends on nothing from its surrounding context. This is sometimes helpful when refactoring.

The real usefulness of `each_with_object`, however, comes when you don't provide a block to it, instead passing it to other code which then uses the resulting enumerator in some way.

```ruby
def print_color_preferences(color_preferences)
	color_preferences.each { |color, name| puts "#{name} likes #{color}" }
end

colors = %w(blue red orange yellow green)

print_color_preferences(colors.each_with_object("Adam"))
```

How is this better than the previous example?

1. `print_color_preferences` is less complex. No `name` variable needs to be passed around. It is just received into the block from `each`.
2. If the logic of `print_color_preferences` were more complex and relied on calling other methods, it would only need to pass `color_preferences` to the called methods, not both `name` and `colors`. The interfaces of these called methods would, themselves, be simpler because of this.
3. `color_preferences.each { ... }` is slightly less busy visually than `colors.each_with_object(name) { ... }`.


---
References:

