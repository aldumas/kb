Write a recursive function to reduce an Iterable to a single value. Do this for all primitive types and generically for reference types. The function signature:

```java
R reduce(Iterable<T> iterable, BiFunction<R, T, R> reducer, R initial)
```