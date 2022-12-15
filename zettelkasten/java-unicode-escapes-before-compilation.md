---
created-at: 2022-12-12 17:44
role: idea
tags: java unicode escapes
---

# Unicode escapes processing time

Unicode escapes are processed prior to compilation. This has some important ramifications.

## Unicode escapes are allowed in program text

Unicode escapes are not relegated to only string and character literals. They can also be used in the program text, itself:

```java
public class Example {
	public static void main\u0028String[] args\u0029 { // unicode-escaped parens
		System.out.println("This compiles and runs just fine.");
	}
}
```

This can cause some confusion. For example, the code below prints an empty string, not a string containing a plus surrounded by parens, as one might expect.

```java
public class Example {
	public static void main(String[] args) { // unicode-escaped parens
		var str = "\u0022+\u0022"; // processes to ""+"" which computes to ""
		System.out.println(str);
	}
}
```

This is because the \\u0022 (quotation marks) escapes are processed prior to compilation and essentially replaced with \" and then the whole file is compiled.

## Unicode escapes are even processed in comments

```java
public class Example {
	public static void main(String[] args) {
		// this call is actually not commented because there's a newline between
		// the line comment characters and the call.
		// \u000a iWillGetCalled();
	}

	private void iWillGetCalled() {
		System.out.println("I got called!");
	}
}
```


#todo fill this out about how unicode escapes are processed before compilation, and give examples of gotchas. Link to java-comments and java-unicode-escapes (once created)

---
# References
