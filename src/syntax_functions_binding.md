### Function binding

> *expr* := *expr* **<>** *expr*

Arguments can be bound to a function with **<>**. Requires that the function,
which should be bound has at least one parameter. The resulting function has
one parameter less, that is, the most left paramter.

Example:

```
func add(x: int32, y: int32): int32
  return x + y
;

add2 := add <> 2 // add2: (func (y: int32) : int32)
io.println(add2(4)) // prints 6
add2_2 := add2 <> 2
io.printon(add2_2()) // prints 4
```
