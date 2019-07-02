## Classes

Classes have attributes, constructors and functions:

- Attributes: Every vardecl in *classcons* and *classunit* which is a
  *vardecl*.
- Constructors: *classcons* is a constructor which has *vardecls* as
  parameters, where every attribute declared in *classcons* is assigned with
  the corresponding argument (the exact same). All other constructors are the
  class's functions which have the exact same name as the class.  Every
  constructor with the additional **_init** function must initialize all
  attributes declared in the class.  The function called **_init** will always
  be called before the constructor function. Constructor functions mustn't
  have a return-type.
- Functions: Every *classunit* which is a *func*, which isn't a constructor.

### Creating an object

An object is created by making function call where the called function
is a reference to the class. The first argument must be **this**.

### Function access

When a class's function is accessed via the class semantic, the returned
function is same as if it would be accessed in a program body.  If the function
is accessed via an object, the returned function is the function accessed via
the class semantic where the first argument is bound with the object.

### Functions

The first parameter of every class's function and constructor must be either
**this** or, if its a function, **This**.