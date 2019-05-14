## Variables

Variables represent values as an identifier. Non-constant members can only be
called, if they aren't constant. Their pointer cannot be changed if they're
immutable (see [Identifier modifiers](./syntax_modifiers.md)). They do not
represent a value as long as they are not definitly initialized. Initializing a
variable is done with the assignments **=** or **:=**. Where the latter is
futher explained in [Variable declaration](./syntax_vardecl.md).

The type of a variable cannot be changed (e.g. via re-assignment).

Example:

```
var0 : int32
// var0 can only be used in assignments not anywhere else
var0 = 0
// var0 can be used
io.println(var0)
```
