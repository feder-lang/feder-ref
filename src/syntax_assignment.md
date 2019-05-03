## Assignment

**=** assigns to the value of *LHS*, which must be a variable, *RHS*. The type
of *LHS* must be the same as *RHS*. Also defines variable *LHS* in the current
context. If variable *LHS* is a global one and the context, where the variable
was declared, and the current context are the same or above, the variable is
defined everywhere, except in contexts, which are in front of the context of
the variable declaration in the run order.
