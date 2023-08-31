---
created-at: 2023-08-31 09:55
tags: dragonruby, labels, align
---

Alignment determines where the text goes relative to the given point. In all cases, the point will be somewhere at the top of the bounding box for the text.

A left-aligned label has the text to the right and below the point.
A center-aligned label has the text centered on the point horizontally but below the point vertically.
A right-aligned label has the text to the left and below the point.

The possible values for `alignment_enum` are `0` (left), `1` (center), and `2` (right). Remember: they go in order from left to right, as would make sense.

By default, labels are right-aligned.

---
References:

