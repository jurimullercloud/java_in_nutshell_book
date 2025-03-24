## String literals

The class definition for class `Account` is stored
in `Account.java` file, and compiled to `Account.class` file.


In Java, strings are objects represented by `String` class.


```java
String html = """
    <html>
        <body>
            ...
        </body>
    </html>"""
```

the compiler finds smallest indentation accross the lines and strips that many white-space
from each line.
To retain full white-space as written.

```java
String html = """
    <html>
        <body>
            ...
        </body>
    </html>
""" // place the closing quotes at the new line
```



## Type literals
Instances of `Class` represent a Java data type and contain metadata about
the type that is referred to.

```java
Class<?> typeInt = int.class;
Class<?> typeIntArray = int[].class;
Class<?> typeAccount = Account.class;
```
