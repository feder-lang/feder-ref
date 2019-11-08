## Use

The first *id* in *idcall* is either a module or library (libraries are
declared with *progname*). If *use* ends with ``.*``, then all public semantics
of *idcall* are accessible in the current environment and all children
environemts otherwise only the semantic referenced by *idcall* can be accessed.

Example:


*hello.feder*:

```
use mod helloprinter
use std.io

func printHello
    io.out.println("Hello, World!")
;
```

*program.feder*:

```
use helloprinter

func main
    io.out.println("Hello, World!")
;
```
