
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

