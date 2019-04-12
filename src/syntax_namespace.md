## Namespace

> *stmt* := **namespace** *id* *newline* *body* **;**

where *id* is the name of the namespace.

A namespace is a *boilerplate* semantic to separated code by functionality.

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
