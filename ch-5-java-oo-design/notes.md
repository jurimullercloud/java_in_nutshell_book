
** The default `toString()` method returns the name of the class and the hex (`0x`) representation of the `hashCode()`
	-> this is to enable equality through `toString()` matching


** for testing if two distinct objects are equal to one another, use `.equals()` method.
	-> note that `Object.equals()` uses `==` equality, meaning it will return true only if the two objects are same objects.

** `instanceOf` will always return `false` if its left side is `null`.

** If a class implements `Comparable` interface (hence implements `compareTo` method) it means a set of object instances is sortable.
	-> note that it is desirable that if `o1.compareTo(o2)` returns true, then `o1.equalsTo(o2)` also return `true`.


** the the design of `clone` method is flawed (it was originally developed to produce deep copies but is inconsistent. an implementer should implement `Clonable<T>` interface and @Override the clone method as public, note that `clone` method is provided by the `Object` class, but the inteface is empty -> marker interface). 

	-> to produce true deep copies a good idea is to implement a copy constructor
```java
Circle original = new Circle(1, 2, 3);
Circle copy = new Circle(original);
```


** interfaces can also define the constants, and any class that inherits it might use it.












