---
created-at: 2023-07-28 09:20
tags: ruby rails
---

```ruby
class Event < ApplicationRecord
	validates :name, :location, presence: true  
	validates :description, length: { minimum: 25 }  
	validates :price, numericality: { greater_than_or_equal_to: 0 }  
	validates :capacity, numericality: { only_integer: true, greater_than: 0 }  
	validates :image_file_name, format: {  
		with: /\w+\.(jpg|png)\z/i,  
		message: "must be a JPG or PNG image"  
	}
	
	...
end
```

`presence` checks that there is a non-blank value. For strings, this means that it must be a string that contains at least 1 non-space character.

> [!NOTE] Keep all validators for a given column together
> This makes it easy to see, at a glance, all the requirements for a given column in one spot instead of needing to scan the full list of validators for references to the column to see which ones apply.

The `allow_blank` validator option can be used to ignore the validator if the column is blank. For example, when used with a `length` validator that sets `minimum` of `25`, the column will still be considered valid if it's a single whitespace (even though there are less than `25` characters). It just deactivates the validator for blank values.

If validations run (e.g. during a call to `save` or `valid?`), errors will be available at `@model.errors`. A couple of useful functions on the returned object:

```ruby
@model.errors.full_messages # => array of error messages
@model.errors.full_messages.to_sentence # => string of comma-separated errors
@model.errors.any? #=> true if there are any errors
```

---
References: