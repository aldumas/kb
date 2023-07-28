---
created-at: 2022-12-12 13:15
role: idea
tags: java javac
---

For a class named `Hello` in package `com.misterinevitable` you compile the program like this, assuming you are in the same directory as Hello.java:

```sh
javac Hello.java
```

Note that you need to include the `.java` extension, and you do not need to include any package information. You can compile the file anywhere, just as long as you provide the path to the file to `javac`. This is different from [[executing-programs|executing the program]] with the java executable.

By default, the compiler will place the generated `.class` file in the same directory as the `.java` file.

