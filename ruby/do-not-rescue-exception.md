---
created-at: 2023-08-04 09:44
tags: ruby
---

In Ruby, the top-level `Exception` class should not be rescued unless the exception is re-raised. This is because Ruby uses some subclasses of `Exception` internally. For example, the functionality to stop a script using `Ctrl-C` is done with a subclass of `Exception`. If you rescue `Exception`, this will also rescue these exceptions preventing the behavior needed to stop the script.

Similarly, you should not inherit directly from `Exception`.

For most cases, you want to rescue `StandardError` if you want to rescue all exceptions that are meant to be rescued. Note that this also rescues exceptions like `NoMethodError` and `TypeError`, but often that is what you want. If not, create or use a subclass of `StandardError` which will not cause these other errors to be rescued.


---
References:

https://rollbar.com/guides/ruby/how-to-handle-exceptions-in-ruby/
https://rollbar.com/guides/ruby/how-to-raise-exceptions-in-ruby/
https://www.honeybadger.io/blog/understanding-the-ruby-exception-hierarchy/