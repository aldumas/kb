---
created-at: 2022-11-30 12:08
role: idea
tags: kotlin idiom takeIf
---

Use `takeIf` to avoid the `else null` pattern:
```kotlin
val x = if (condition) obj.method() else null

// becomes

val x = obj.takeIf { condition }?.method()

