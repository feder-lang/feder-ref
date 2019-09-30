## Use

The *idcall*s following the use keyword are either variables or namespaces.
All public-visible semantics of the variable or namespace will be added to the
current environment. Semantics defined in the current environment have
precedence (semantics added with **use** cannot shadow semantics in current
environment *and* parent environments).

Example:

```
mod mymod
	func printHello
		io.println("Hello, world!")
	;
;

func main
	use mymod
	printHello()
;
