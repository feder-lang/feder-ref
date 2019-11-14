## Variables

Private and mutability:

- Variables starting with '\_' are private variable and can only be reached by
  the current environment and current environment's children

- Variables starting with an uppercase character (optionally with leading '\_')
  are called **value immutable**. Their environment has only **immutable**
  functions (functions starting where the first parameter is **value
  immutable**) and **immutable** variables, where **mutable** variables in the
  original environment will also be **immutable**.

- Variables which have the type ``&expr`` are **pointer mutable**. They can be
  reassigned after initialization. Variables with other types cannot be
  reassigned. Conversion between pointer (im-)mutable types is done implicitly.

Example:

```
&x := 100
x = 101 // works
y := 100
y = 101 // doesn't compile
```

### Representing an object

A variable returns ``()`` if it isn't initialized.  A variable can be
initialized using **=** or **:=** to declare and define the variable at the
same time.

### Assignments

Assigning a variable with **=** (re-)initializes the variable. Reinitialization
[^reinit] is only possible if variable is **pointer mutable**. The assigned
object (RHS) is returned.

Assigning a variable with **:=** declares the variable and the initializes
the variable. Returns ``()``.

[^reinit]: The variable is already initialized.

### Local and global

**Local** variables are dropped after a *funcbody* scope ends. **Global**
variables are dropped when the program terminates.

### Shadowing

With *shadowing* identifiers used by previous variable declarations can be used
in another variable declaration. Afterwardss, as long the new variable isn't
dropped, this variable will be referenced when mentioning the identifier
instead of the old one. A variable can only be shadowed if it was declared
in a parent scope.

### Initialization

The value of a *funcbody* variable can be used, if the variable was definitly
initialized, otherwise only initialization is allowed. The initization of
variables in *funcbody* can only be done in the scope the variable was
declared.
