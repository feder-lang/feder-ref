## Classes

Classes have attributes, constructors and functions:

- Attributes: Every vardecl in *classcons* and *classunit* which is a
  *vardecl*. Added to the environment of the an object which has the type
  of the class.
- Constructors: *classcons* is a constructor which has *vardecls* as
  parameters, where every attribute declared in *classcons* is assigned with
  the corresponding argument (the exact same). All other constructors are the
  class's functions which have the exact same name as the class.  Every
  constructor with the additional **_init** function must initialize all
  attributes declared in the class.  The function called **_init** will always
  be called before the constructor function. Constructor functions mustn't
  have a return-type.
  Contructors are added to the parent environment of the class.
- Functions: Every *classunit* which is a *func*, which isn't a constructor.

The name of the class (second expression *id* in *classdecl*) must start with
an uppercase character with optional leading '_'.

### Implementing traits

Functions declared can be implemented by classes to support polymorphism.
*traitimpl* must contain all functions declared by the mentioned trait
after **:** in *traitimplbody*. A trait already implemenated in the functions
cannot be reimplemented.

### Creating an object

An object is created by making function call where the called function
is a reference to the class. The first argument must be **this**.

### Function access

When a class's function is accessed via the class semantic, the returned
function is same as if it would be accessed in a program body.  If the function
is accessed via an object, the returned function is the function accessed via
the class semantic where the first argument is bound with the object.

### This

This must only be used in an class expression. It represent the closest class
type.

### Functions

The first parameter of every class function must have the same type as the
class. This can be achieved with [This](./expr_class.md#This). If the first
parameter doesn't have a variable name (just the type), then the variable
**this** with current class as type is added to the environment of the function
body.

Functions are added to the environment of the class semantic and
are added to class' instances without the first parameter.
