---
created-at: 2022-11-30 12:10
role: idea
tags: kotlin idiom map.getOrDefault
---

Use `Map::getOrDefault` and similar functions to avoid usage of a control structure when mapping a key to a value, defaulting to the key if it does not exist in the map:
```kotlin
val x = if ("key" in map) map["key"] else "key"

// becomes

val x = map.getOrDefault("key", "key")

