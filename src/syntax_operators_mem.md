### Member access

> *expr0* **.** *id*

where *id* is an accessable semantic (e.g. functions, variables, attributes) in
the semantic of *expr0*. If the referenced semantic is private, *expr0* has to
be **this** or **This** to access *id*.

Example:

```
namespace hello
  func world
    io.println("Hello, World!")
  ;
;

hello.world()
```
