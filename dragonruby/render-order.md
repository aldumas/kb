---
created-at: 2023-09-02 21:59
tags:
  - dragonruby
---
## Render Order [link](http://docs.dragonruby.org.s3-website-us-east-1.amazonaws.com/#---render-order)

Primitives are rendered first-in, first-out. The rendering order (sorted by bottom-most to top-most):

- `solids`
- `sprites`
- `primitives`: Accepts all render primitives. Useful when you want to bypass the default rendering orders for rendering (eg. rendering solids on top of sprites).
- `labels`
- `lines`
- `borders`
- `debug`: Accepts all render primitives. Use this to render primitives for debugging (production builds of your game will not render this layer).

This means you have limited control over how these items overlap. Within a category, you can control the order you add them. But you cannot expect to paint over a line with a solid. The line will always appear on top of the solid since solids are rendered first. This can be bypassed by using primitives.

#todo Figure out the full render order.


---
References:

