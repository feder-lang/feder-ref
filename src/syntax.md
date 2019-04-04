# Expressions

This chapter covers all expressions and statements, which can be used in Feder.
There are two important non-terminals: *expr* and *stmt*. *expr* is an
expression, which are used in statements. And *stmt* are statements, which
can be used as *lines* in a program.

> *program* := *body* **EOF**\
> *body* := e | *stmt* | *stmt* *newline* *body*\
> | *body* *newline* **return** *expr*?

where *expr* mustn't be used if current scope doesn't accept return-types.
**return** *expr* is required if scope requires return type, except if
the last statement was an if or match expression.
