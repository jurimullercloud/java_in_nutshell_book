There 5 fundamental reference types in Java:
 - classes
 - interfaces
 - enums - specialized kind of class
 - arrays
 - annotations - specialized kind of interface

** Instances of a class is also the instance of the underlying interface type.

** Any class with declared members of kw `abstract` should also be marked as abstract.


### Field Declaration Syntax
`volatile` modifier indicates that the value of the field should only be read from the main memory (but not from cache made by threads on a register and CPU cache.)



### Field Initialization with default values
```java
public class SampleClass {
	public int len = 10;
	public int[] table = new int[len];

	public SampleClass() {
		for(var i = 0; i < len; i ++) {
			table[i] = i;
		}	
	}
}
```

When compiled by javac the default values of fields are automatically injected into the constructor.
As given below:
```java
	public SampleClass() {
		len = 10;
		table = new int[len];
		for(var i = 0; i < len; i ++) {
			table[i] = i;
		}	
	}
```


### Static Variable loading
When the code is first compiled the Java compiler implicitly creates a class initialization method  (the compiled name of the method is `<clinit>`) the body of which loads the static fields values onto memory. This method is called the first time the class is loaded by JVM into the memory and populates the values.
 -> The values are initialized in the order they appear on the source code.

Apart from that there is `static` initializer that will be placed on the body of class initialization method
```java
static {
	double x = 5.5;
	for // perform something programmatic here
}
```

A class may have any number of static initializers and it cannot use the `this` keyword.


### Record Constructors

A specialized constructor, the default ctor of record should be instantiated within this ctor.
```java
public record Point(double x, double y) {
	public Point(double x) {
		this(x, 0.5);
	}
}
```

A compact constructor -> used for validating the default constructor parameters. Apart from that it implicitly instantiates the record value.
```java
public record Point(double x, double y) { // the top one is called canonical constructor
	public Point {
		if (Double.isNan(x) || Double.isNan(y)) {
			throw new IllegalArgumentException("illegal nan");
		}
	}
}
```

### Method overriding
Given the super and sub-classes, if a subclass overrides the method foo() of super-class. If e is the instance of the sub-class, there is no way of calling the super-class' foo() method using e (from outside). Inside the sub-class it can be called  using `super().foo()` call.

```java
public class Super {
	
	public void foo() {
		System.out.println("super foo");	
	}
}

public class Sub : Super {
	@Override
	public void foo() {
		System.out.println("sub foo");	
		super.foo();
	}
}



public static void main(String[] args) {
	e = new Sub();
	e.foo();
}
```


### Modifiers

if a class member is declared `protected` it is accessible within the same package as well as to all the sub classes of a class.

** A class can only access protected fields within its own type. Hence the following is illegal


```java
public class A {
	protected int foo = 5;
}

public class B : A {
	public void examine(A a) {
		a.foo; // THIS IS ILLEGAL
	}

	public void examine(B b) {
		b.foo; // THIS IS LEGAL
	}
}
```


** Constructors are not inherited, **they are chained**.





