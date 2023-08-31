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

Lazy load a property on first use:

```ruby
def property
	@property ||= expensive_calculation
end
```

If you don't want to define `expensive_calculation` as a method, you can embed the logic in a lambda and immediately call it:

```ruby
def property
	@property ||= lambda { ... code returning computed property ... }.call
end
```

---

Given a `Hash` parameter, provide default values for keys but override with matching ones from the parameter:

```
def some_method(**args)
	params = { status: "A" }.merge(args)
	...
end
```

---
References:






