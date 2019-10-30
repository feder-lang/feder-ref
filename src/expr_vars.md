## Variables

Private, constant and mutability:

- Variables starting with '\_' are private variable and can only be reached by
  the current environment and current environment's children

- Variables starting with an uppercase character (optionally with leading '\_')
  are called **immutable**. Their environment has only **immutable** functions
  and **immutable** variables, where **mutable** variables in the original
  environment will also be **immutable**. Defined constant variables must not
  be reassigned.

### Representing an object

A variable returns ``()`` if it isn't initialized.  A variable can be
initialized using **=** or **:=** to declare and define the variable at the
same time.

### Assignments

Assigning a variable with **=** (re-)initializes the variable. Reinitialization
[^reinit] is only possible if variable is **mutable**. The assigned object
(RHS) is returned.

Assigning a variable with **:=** declares the variable and the initializes
the variable. Returns ``()``.

[^reinit]: The variable is already initialized.

### Local and global

**Local** variables are dropped after a *funcbody* scope ends. **Global**
variables are dropped when the program terminates.
