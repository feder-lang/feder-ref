## Capabilities

Capabilities are for ensuring functionality and casting semantics.

> *expr* := *expr0* **@** *caps*\
> *caps* := *ids*

Where an *id* in *ids* must one of:

- **Safe**: Ensure safety (only safe dynamic allocations must be used). Ensures
  every operation in the associated *expr0*, is [*safe*](./syntax_safe.md).
  This includes constructors **AND** functions.
- **This**: Allow access to private members of semantic *expr0*. *expr0* has to
  be a class instance.
- **Const**: Only allow constant access to semantic *expr0*.
- **Value**: Cast to r-value or R-Value type (functions).
- **Unique**: Ensure there's no other semantic named the same in the current
  context (works only with named semantics).
- **Var**: Used in function return-type for returning a handle to a variable.

Two *id*s of the same type aren't allowed in *caps*.

Examples:

Unique:
```
class Person
  // Private modify function
  func@Safe,Unique _modify
  ;
;

// Call modify
Person()@This._modify()
```

Var:
```
class{T} TwoTuple
  mut x0: T
  mut x1: T

  func TwoTupe(x0: T, x1: T)
    .x0 = x0
    .x1 = x1
  ;

  // Returns reference to variable x0
  func fst : T@Var
    return x0
  ;

  // Returns reference to variable x1
  func snd : T@Var
    return x1
  ;
;

t0 := TwoTuple(100, 101)
t0.fst() += 100
io.println(t0.fst()) // prints 200
```
