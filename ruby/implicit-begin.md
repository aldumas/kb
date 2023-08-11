---
created-at: 2023-07-28 09:16
tags: ruby
---

In ruby, the beginning of a method `def` constitutes an implicit `begin`.

```ruby
def foo
	#code
rescue => e
	#code
end
```

This is considered to be better than the explicit `begin`.

```ruby
def foo
	begin
		#code
	rescue => e
		#code
	end
end
```

---
References:




