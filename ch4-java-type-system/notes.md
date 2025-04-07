** If a class implements an interface but does not provide implementations of methods defined by it, the class must be declared `abstract` (as by definition all methods of an interface are implicitly `abstract`).


as the classes are extending a superclass and can be treated as instances of them, they can also be treated as the interface it implements:
```java
public interface Centered {}
public class Shape {}

public class Circle extends Shape implements Centered {}
public class Square extends Shape implements Centered {}

public static void main() {
	List<Shape> shapes = new List<Shape>();
	List<Centered> centeredShapes = new List<Centered>();
}
```





## Generics
 ** In Java the generics work only at compile time 
	 -> when `javac` compiles the source code. The following code:
 ```java
 interface OrderCount {
	int totalOrders(Map<String, List<String>> orders);
	int totalOrders(Map<String, Integer> orders);
 }
```

will be compiled to :
```java
int totalOrders(Map orders);
```
thus it will the `OrderCount` is illegal.
This is called **type erasure**.

### Bounded Type Parameters
```java
public class Box<T> {
	protected T value;
	public void box(T t) {
		value = t;
	}	
	
	public T unbox() {
		T t = value;
		value = null;
		return t;
	}
}
```
If we want to implement a box that holds only numeric types. We can further restrict our constraints on Box type.

```java
public class NumberBox<T extends Number> extends Box<T> {
	public int intValue() {
		return this.value.intValue();
	}
}
```

`this.value.intValue()` is possible because, type of value which is T has super class of `Number`.

In Java the generic types are **invariant** not **covariant**

```java
// EXAMPLE OF COVARIANCY 
String[] words = {"Hello", "World!"};
Object[] arr = words; 
```

```java
// THIS CODE WON'T COMPILE
List<Object> objs = new ArrayList<String>();
```


## Lambda Expressions and FP

** Lambdas are implemented using **method handles** and a special JVM bytecode called `invokedynamic`.

Lambda expression -> creation of an object of specific type:: target type.
	** Only certain types are eligible to be target type of lambda.
	** target types are also called functional interfaces 
		- they must be interfaces.
		- have only one **nondefault** method


As a result:
```java
Runnable r = () -> System.out.println("Hello");
```
creates an object of type `Runnable`. The method assigned is only run when we invoke `r.run();`

In order for javac to compile a particular lambda expression, the following must be met by it:
	- the lambda must appear where an instance of an interface type is expected.
	- The expected interface type should have exactly one mandatory method.
	- The expected interface method should have a signature that exactly matches that of a lambda expression.

If these conditions are met, the runtime creates an instance of the interface and injects body of the lambda expression to the mandatory method.



Example, java.io.File class has `list()` method which lists files in a given directory. it accepts a `FilenameFilter` object to filter the files to accept or reject.

```java
@FunctionalInterface
public interface FilenameFilter {
	boolean accept(File dir, String name);
}


File dir = new File("/src");
String[] fileList = dir.list(
	(dir, fileName) -> fileName.endsWith(".java") 
);
```



## Nested Types


## Local classes
Even though the definition of the class is local, when JVM exits the method scope, the instances of the class may live beyond that.



## Anonymous Classes
```java
public class Animal {
	public void sound() {}
}

public static void main() {
	Anumal a = new Animal() {
		@Override	
		public void sound();
	}

	Runnable r = new Runnable() { // for multi-threading
			@Override	
		public void sound();	
	}
}
```









