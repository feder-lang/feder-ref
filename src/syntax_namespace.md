## Namespace

> *stmt* := **namespace** *id* *newline* *body* **;**

where *id* is the name of the namespace.

A namespace is a *boilerplate* semantic to separated code by functionality.
Every *stmt* in *body*, which is either a function, class, trait, enum or
variable, are **members** of the namespace.

Example:

```
namespace mystd
  func myprintln(str : std.String)
    std.io.print(str)
    std.io.print("\n")
  ;
;

mystd.myprintln("Hello, World!")
```
