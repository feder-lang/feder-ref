### Variable declaration

> *stmt* := *vardecl*\
> *vardecl* := *id* **:** *expr0* | **mut** *id* **:** *expr0*

where *expr0* is a type or tuble composed of types. The declared variable will
be called *id*. A type is either an array-type, class, trait, enum or primitive
type. When using a tuple as type, every tuple member must have a variable name.

> *stmt* := *id* **:=** *expr1* | **mut** *id* **:=** *expr1*

where *expr1* is a value. The type of the variable called *id* is the type of
*expr1*. The value of the variable will be the value of *expr1*.

Examples:

```
val0: uint32        // Integer
a0: uint32[]        // Array
t0: (uint32, int32) // Tuple

// Tuples:

myTuple: (x : i32, y : i32)
myTuple = (10, 11)
myTypleRe := (10, 11)
io.println(myTuple.x)
io.println(myTuple.y)

// mutable vars
mut x : i8
```
