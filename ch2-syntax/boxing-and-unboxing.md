The Java Platform includes *wrapper classes* around primitive types
`Boolean`,  `Byte`, `Short`, `Character`, `Integer`,  `Long`,  `Float`,  `Double`
	-> immutable, final classes. 

** usually used when storing primitive values in collections:

`List<Integer> numbers = new ArrayList<>();`
`numbers.add(Integer.valueOf(-1));`
`int i = numbers.get(0).intValue();`

The type conversion is boxing (primitive -> wrapper) and unboxing (wrapper -> primitive). The boxing and unboxing are performed automatically so collectively it is called autoboxing.  


