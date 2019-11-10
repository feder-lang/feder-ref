## Arrays

Arrays can store multiple elements. The elements are accessed with an index (an
*uintptr* value) starting from 0. *arraylit* returns **Array{type}**, where
type is the type of the value *expr0*. Every value in the comma separated
*expr1* must have the exactly same type as *expr0*. The length of the array is
1 + count of commas in *expr1*.  *arraycpy* returns **Array{type}**, where type
is type of the object *expr0* and every element of the array has the value of
*expr0* and the array's length is determined by *expr1*. *expr1* must return
the type *uintptr*.  *arrayempty* returns an array with length 0 with the type
**Array{type}**, where type is an the type referenced by *expr*. Here, *expr*
mustn't contain a comma (would collide with *arraylit*. *arrayfor*'s *id* is an
index variable which will have all values between including 0 till excluding
value of *expr0*. Every *id*th element will be assigned to value returned
by *retfuncbody*.

Example:

```
Array{int32} myarray = [1,1,2,3]
null std.io.println(myarray[0]) // print 1
null std.io.println(myarray.length()) // print 4

null std.io.println([i32].length()) // prints 0

// for-arrays
squared := [for i : 20
    return i * i
]

null std.io.println(squared[10]) // prints 100
```
