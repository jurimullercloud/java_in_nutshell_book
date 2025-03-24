
** As Jave does not allow for code to run on its own outside of a class,
the lambda functions is then an anonymous method of an anonymous class
once the code is compiled.


```java
Runnable r = () -> System.out.println("Hello, World");
```


```java
ActionListener listener = () -> {
    System.out.println("Event fired at: "+ e.getWhen());
        System.out.println("Event command: "+ e.getActionCommand());
}
```
