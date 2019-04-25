## Capabilities

Capabilities are for ensuring functionality and casting semantics.

> *expr* := *expr0* **@** *caps*\
> *caps* := *ids*

Where an *id* in *ids* must one of:

- **Safe**: Ensure safety (only safe dynamic allocations must be used). Ensures
  every operation in the associated *expr0*, is [*safe*](./syntax_safe.md).
  This includes constructors **AND** functions.
- **This**: Allow access to private members of semantic *expr0*. 
- **Const**: Only allow constant access to semantic *expr0*.

Two *id*s of the same type aren't allowed in *caps*.
