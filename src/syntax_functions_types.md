### Functions as types

> expr := **func** *params*? *return-type*?

Guards are not allowed. Represents a function with *params* and optional
*return-type*.

When using a declared function as a value, the function must be **Unique**.

Example:

```
// Create a function
func@Unique add(x : int32, y : int32): int32
  return x + y
;

fun: (func (int32, int32) : int32)
fun = add
```
