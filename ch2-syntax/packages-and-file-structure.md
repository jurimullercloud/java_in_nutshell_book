

### Static imports
The static import syntax can also be used to import the enum members:
```java
package climate.temp;
enum Seasons {WINTER, SPRING, SUMMER, AUTUMN};

// in other file
imoort static climate.temp.Seasons.*;
```


** Each .java file is allowed only single `public` class to be defined which should be the same with the file name itself.
	-> Account.java:: `public class Account{}` -> compiled :: Account.class


The classfiles are by default located under the directory of its current subpackage:
	-> `com.name1.name2.Account.class`

If the packages are located in a directory other than the current directory, use `--classpath` flag when invoking the interpreter or set `CLASSPATH` environment variable.


The Java program is run by executing **the fully qualified** name of the class that contains the `main` method -> !! not the name of the class file.
 -> The interpreter exits when the `main` method returns, or **if `main` spawned any other threads it waits for all threads to exit**.

```bash
java -classpath /opt/Jude com.davidflagnan.jude.Jude dataFile.jude
```

`/opt/Jude` where the .class files are located


If the all the auxiliaries of a java program is archived in .jar file, a Java program can be run using:

```bash
java -jar /usr/local/log-analyzer/log-analyzer.jar
```


** Java 17 allows to run java programs directly from the source files, providing it still contains the `main` method and a class defined to match the file name:

```bash
java MyClass.java
```









