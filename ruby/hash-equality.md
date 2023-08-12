---
created-at: 2023-08-12 13:06
tags: ruby
---

There's a special form of equality that lies in between the strict [reference equality](ruby/reference-equality.md) provided by `equal?` and the flexible [value equality](ruby/value-equality.md) provided by `==`. This is implemented in the `eql?` method, which I am referring to as *hash equality*.

When searching for a key in a hash map, the hash map implementation must:
1. Find the place to look for the keys, the bucket. It does this using the provided key's `hash` method.
2. Examine all the keys in the bucket and determine if any are equal to the provided key. It needs to do this because different objects of different types could all map to the same bucket.

If `Hash` had been defined to use `equal?` when comparing keys in the bucket, it would mean you could only retrieve values if you had the same exact object you used to insert the value with, which might not be available anymore.

On the other hand, if `Hash` had been defined to use `==` it would mean you could not be as precise when storing or looking for values. For example, you could not use `1` and `1.0` in the same `Hash` to store different values since numeric values will cast over `==` and then compare as equal.

For this reason, an intermediate form of equality is used that usually takes into account the class of the key as well as value equality of the key.

The `Object` class defines `eql?` and `==` to be the same (`equal?`), and subclasses which override `==` tend to follow suit with something like this:

```ruby
alias :eql? :==
```

Classes which override `==` to allow comparing objects of *different* types will typically override `eql?` to compare object class in addition to value equality so that keys will only match if their classes are the same.

>[!Important]
> Due to the way key lookups in hash tables work, it's important that the following relationship holds:
> 
>  if `a.eql? b` then `a.hash == b.hash`

That is, if two keys compare as equal according to `eql?` then their hash values must also be equal.

To see why, consider what would happen if you added a key to a `Hash` and then tried to look it up using an object which compares as `eql?` but has a different hash value. The first thing the `Hash` would do is try to determine which bucket to look in, which it does by calling `hash` on the key you're looking up with. The hash value will likely map to a different bucket than the one for the key used when inserting the value. It looks in this bucket and does not find any keys (or it finds unrelated keys which it checks your key against using `eql?` and finds out they don't match) and then it gives up and determines the key is not in the `Hash`. It needs to be able to assume the hash value of the key you are using to look up with will lead it to the same bucket as the hash of the key stored in the `Hash`.

For this reason, whenever you define `eql?` you need to determine whether you need to override `hash` to ensure that the hash values will always match for two objects that compare as equal using `eql?`.

---
References:

