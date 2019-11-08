## Arrays

Arrays can store multiple elements. The elements are accessed with an index (an
*uintptr* value) starting from 0. *arraylit* returns **Array{type}**, where
type is LHS of *expr* (length = count of comma operator + 1), if *expr* is an
binary operator expression using comma, otherwise the type of of *expr* (length
= 1).  *arraycpy* returns **Array{type}**, where type is type of the object
*expr0* and every element of the array has the value of *expr0* and the array's
length is determined by *expr1*. *expr1* must return the type *uintptr*.
*arrayempty* returns an array with length 0 with the type **Array{type}**,
where type is an the type referenced by *expr*.

Example:

```
Array{int32} myarray = [1,1,2,3]
null std.io.println(myarray[0]) // print 1
null std.io.println(myarray.length()) // print 4
```
