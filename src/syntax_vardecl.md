### Variable declaration

> *stmt* := *vardecl*\
> *vardecl* := *id* **:** *expr0*

where *expr0* is a type or tuble composed of types. The declared variable will
be called *id*. A type is either an array-type, class, trait or enum. When
using a tuple as type, every tuple member must have a variable name.

> *stmt* := *id* **:=** *expr1*

where *expr1* is a value. The type of the variable called *id* is the type of
*expr1*.

Examples:

```
val0: uint32        // Integer
a0: uint32[]        // Array
t0: (uint32, int32) // Tuple

// Tuples:

myTuple: (x : int32, y : int32)
myTuple = (10, 11)
io.println(myTuple.x)
io.println(myTuple.y)
```
