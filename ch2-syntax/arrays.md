** In java, the multidimensional arrays are not treated as true matrix like arrays like in
C or C++
  -> in which the entire multidimenstional array is stored as contegious block
        of memory.

  -> This allows Java multidim arrays to be jagged>



  ** Arrays implement `Clonable` interface, meaning the class to `clone` always
  produces a clone.
  ** also `Serializable`

### Array widening conventions

Because Arrays extend `Object` and implement `Serializable` and `Cloneable`
An array type can be widened to other array types.
If array type is reference type `T` and `T` is subtype of `S`, then array of `T` can be
subtyped to array of `S`.


```java
String[] arrayOfStrings;

Object o = arrayOfStrings;
Clonable c = arrayOfStrings;
Serializable s = arrayOfStrings;
```

** This ability of widening means that the compile time type of arrays are not same
as their runtime type.


** This type widening is also called array covariance.

** In Java the array initializatio happen at the runtime not at the compile time
e.g

```java
int[] perfectNumbers = {6, 28}; // is compiled to
// -------
int[] perfectNumbers = new int[2];
pefectNumbers[0] = 6;
pefectNumbers[1] = 28;
```

This has the important corralary:
  -> the array elements need not to be compile time constants, thus the following
  code is legal

```java
Account[] accounts = { findAccountById(1), findAccountById(2) }; // is compiled to
```
