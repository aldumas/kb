Write a recursive function to reduce an Iterable to a single value. The function signature:

```java
R reduce(Iterable<T> iterable, BiFunction<R, T, R> reducer, R initial)
```