## Ensure

The *ensure* expression can tell the compiler that the variable *idcall* has
specific properties. This can be further used to call functions with guards.
If the *ensure* expression has an else-clause it is possible for the
expression to return a value.

Example: Safe division

```
std.io.out.print("Input LHS value: ")
lhs := std.io.in.readf64()
std.io.out.print("Input LHS value: ")
rhs := std.io.in.readf64()

ensure rhs != 0.0
    result := lhs / rhs
    std.io.out << "Result: " << reuslt << std.io.endl
;
// rhs / lhs fails to compile
```
