---
created-at: 2023-09-02 22:33
tags:
  - dragonruby
---
The point given when specifying a solid is not actually the lower-left hand point of the rectangle. The x-value matches, but the y-value is 1 below the actual y-value of the solid. Solids behave as if their upper-left hand point should have been the fixed point, but they decided to make it the lower-left hand, and did this by:

```ruby
# Let's create a rectangle with this upper-left point and height:
upper_left_point = {x: 100, y: 100}
height = 50

solid_position = {x: upper_left_point[:x], y: }
```


---
References:

