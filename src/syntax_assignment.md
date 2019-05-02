## Assignment

**=** assigns the value of *LHS*, which must be a variable, to *RHS*. The type
of *LHS* must be the same as *RHS*. Also defines variable *LHS* in the current
context. If variable *LHS* is a global one and the context, where the variable
was declared and the current context are the same, the variable is defined
everywhere, except if the context is in front of the one of the variable in the
run order.
