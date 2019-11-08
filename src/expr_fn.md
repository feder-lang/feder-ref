## Functions

Normal functions can't use non-global variables from parent environments.

A function beginning with a lowercase character with possible leading '\_', no
function with the same parameters and function name must exist in the current
environment. Otherwise, if the function starts with a uppercase character with
possible leading '\_', no other semantic with the same name must exist in the
current environment.

If the *idcall* before the function's parameters consist of multiple *id*s
the function called like the most right *id* is added to the environment
referenced to be the *id*s in fron of the last one. The environment
has to be a [class](./expr_class.md), [module](./expr_mod.md)
or primitive datatype.

A function with no *retfuncbody* or *return-type* returns the empty tuple ``()``.
A function with a return type (a function with **:** after the parameters or
function name) must not have the return type **()** (empty type).

Only functions which are declared with the **Unique** capabilitiy can be used
as an object, all others must only be used for complete function calls.

Example (functions without return type):

```
// print hello world
func printHello0(out: OutputStream)
  null out.println("hello, world!")
;

// multiple instructions
func printHello1(out: OutputStream, user: String)
  null out.print("hello, ")
  null out.print(user)
  null out.print("!")
;
```

Example (functions with return type):

```
/*
 * How to write a function which returns the sum of the first and second
 * argument in Feder
 */

// sum function with **return** keyword and explicit return-type
func add0(x: int32, y: int32): int32
  return x + y
;

// sum function with **return** keyword and implicit return-type
func add1(x: int32, y: int32):
  return x + y
;

// sum function without **return** keyword but explicit return-type
func add2(x: int32, y: int32): int32 =
  x + y
;

// sum function with **return** keyword and implicit return-type
func add3(x: int32, y: int32) =
  x + y
;
```

### Guards

The *expr0* of the guard has to evaluate to an object with the type *bool*.  If
*expr0* evaluates to **True** nothing happens, the functions is called normally
(other guards are respected of course). Otherwise a panic is generated,
if **=>** isn't following *expr0*, or *expr1* is returned. The returned object
must be the same type as the return-type, of course.

The guard can be checked at compile, if possible and must be checked during
return-time. The guard of the function definition (with *funcbody*) has
precedence.

Example:

```
// Division with Division-by-zero exception
func div(x: int32, y: int32 | y != 0): int32 =
  x / y
;

// Dvision with Division-by-zero returns 0
func div(x: in32, y: int32 | y != 0 => 0): int32 =
  x / y
;
```

### Argument binding

The operator **<>** is used to bind a function (LHS), which is also a
variable/anonymous function, to an object (RHS) which replaces the last
parameter. The function must have at least one parameter. The returned function
is is missing the last parameter. Values are bound by using call-by-value.

```
// normal integer addition
func add(x: int32, y: int32): int32 =
  x + y
;

// sum number one and argument and return result
add1 := add <> 1

func main
  null io.out.println(add1(2)) // prints 3 to standard output
;
```

### Function body

Every *expr* (but not *expr* in *expr*) is a statement. These statements must
return *()* as type or an L-value. Otherwise the *expr* is invalid. This can
be fixed with the **null** operator.

### Function call

A function is called with *expr* **(** x **)** where x is either nothing, a
value or tuple of values. The *expr* value count must be the same as the
parameter count of the function declaration. Values (and variables) are passed
by using call-by-value.

Example:

```
func add(x: int32, y: int32) =
  x + y
;

func main
  null add(2, 3)
;
```

Invalid add function calls:

```
add(2) // invalid argument count, no add(x: int32) function declaration
add(2.0f, 3) // invalid argument 2.0f (not type int32),
             // no add(x: float32, y: int32) function declaration
```
