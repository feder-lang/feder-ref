### Variable declaration

> *stmt* := *vardecl*\
> *vardecl* := *id* **:** *expr0*

where *expr0* is a type or tuble composed of types. The declared variable will
be called *id*. A type is either an array-type, class, trait or enum.

> *stmt* := *id* **:=** *expr1*

where *expr1* is a value. The type of the variable called *id* is the type of
*expr1*.
