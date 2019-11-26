## Tuples

A tuple is a primary expression **(** *expr* **)**,
where at least *expr* is a binary operator **,** comma expression.

A tuple with **&** *id* or *id* as elements must be the the left
hand side of the **:=** assignment. Tuples with *vardecl* as elements
must be the left hand side of the **=** assignment. Tuples with just
types must be a function's result-type. Tuple with just values as elements
must be a the function's return-value, but can also be used in normal code.
In the last case the are expanded, as if you would have written the contents
with surrounding brackets. Thus

```
myfunc(hello, (1, 2, 3), 4)
```

is transformed to

```
myfunc(hello, 1, 2, 3, 4)
```

The rules are:

- First every tuple that is in a tuple is expanded, afterwards itself will
  be expanded
- As the comma operator is left associative, the most left element will be
the first on to be removed from the tuple and added to the left side. While
the operator on the left is automatically removed.
