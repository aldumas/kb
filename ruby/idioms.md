---
created-at: 2023-08-12 14:32
tags: ruby
---

Append a value to an array only if it does not already exist:

```ruby
animals = ["lion", "bear", "rabbit"]

animals |= ["bear"] # uses union operator, equality is checked with eql?
```

---

Set a value if it has not been set, returning the result regardless:

```ruby
def property
	@property ||= expensive_calculation
end
```

If you don't want to define `expensive_calculation` as a method, you can embed it in a lambda and immediately call it:

```ruby
def property
	@property ||= lambda { 
end
```

---
References:






