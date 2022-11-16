This is a collection of idioms and patterns to use when writing Kotlin code. In general, when writing Kotlin code, try to consider how to write it in a way that minimizes usage of temporary variables and control structures. Try to write in a readable functional way.

- - -

Use `takeIf` to avoid the `else null` pattern:
```kotlin
val x = if (condition) obj.method() else null

// becomes

val x = obj.takeIf { condition }?.method()
```

Use `Map::getOrDefault` and similar functions to avoid usage of a control structure when mapping a key to a value, defaulting to the key if it does not exist in the map:
```kotlin
val x = if ("key" in map) map["key"] else "key"

// becomes

val x = map.getOrDefault("key", "key")
```

- - -
These are some patterns I need to find idioms and patterns for.

Invoke different and unrelated behavior depending on whether a value is `null`.
```kotlin
val x = if (arg == null)
	methodA()
else
	methodB(arg)

// becomes

val x = arg == null ? methodA() : methodB(arg)

```