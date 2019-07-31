## Functions

Normal functions can't use non-global variables from parent environments.

A function beginning with a lowercase character with possible leading '_', no
function with the same parameters and function name must exist in the current
environment. Otherwise, if the function starts with a uppercase character with
possible leading '_', no other semantic with the same name must exist in the
current environment.

If the *idcall* before the function's parameters consist of multiple *id*s
the function called like the most right *id* is added to the environment
referenced to be the *id*s in fron of the last one. The environment
has to be a [class](./expr_class.md), [module](./expr_mod.md)
or primitive datatype.

A function with no *retfuncbody* or *return-type* returns the empty tuple ``()``.

Only functions which are declared with the **Unique** capabilitiy can be used
as an object, all others must only be used for complete function calls.

### Guards

The *expr0* of the guard has to evaluate to an object with the type *bool*.  If
*expr0* evaluates to **True** nothing happens, the functions is called normally
(other guards are respected of course). Otherwise a panic is generated,
if **=>** isn't following *expr0*, or *expr1* is returned. The returned object
must be the same type as the return-type, of course.

The guard can be checked at compile, if possible and must be checked during
return-time. The guard of the function definition (with *funcbody*) has
precedence.

### Argument binding

The operator **<>** is used to bind a function (LHS), which is also a
variable/anonymous function, to an object (RHS) which replaces the last
parameter. The function must have at least one parameter. The returned function
is is missing the last parameter.

### Lambda expressions

Lambda functions can also use non-global variables from a parent environment in
*retfuncbody*. They are equivalent to normal *functions* which have these
variables as additional parameters and are then bound to the function (via
**<>**).

### Function body

Every *expr* (but not *expr* in *expr*) is a statement. These statements must
return *()* as type or an L-value. Otherwise the *expr* is invalid. This can
be fixed with the **null** operator.
