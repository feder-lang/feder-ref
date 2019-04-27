# Expressions and statements

This chapter covers all expressions and statements, which can be used in Feder.
There are two important non-terminals: *expr* and *stmt*. *expr* is an
expression, which are used in statements. And *stmt* are statements, which
can be used as *lines* in a program.

> *program* := *external*? *body* **EOF**
> *external* := *includes* *newline* *imports* | *includes* | *imports*\
> *includes* := *include* | *include* *newline* *includes*\
> *include* := **include** *string* 
> *imports* := *import* | *import* *newline* *imports*
> *import* := **import** *idcall*

Where *string* is a unix file path. The files semantics will be added to the
lookup-path of the current file. A file must only be included one time in a
file. A file mustn't include itself. A *include* also determines the run order.
A file included with a simple *include* will be executed before the 'current
file', the included file mustn't have a included the 'current file'.

The first *id* of *idcall* name of the package to import. Subsequent *id*s are
used to include a selected semantics in the package. When only the package is
imported, a namespace called like the package will be added to the lookup-path
of the 'current file', which contains the semantics of the package.
Double-dependencies are not supported.
