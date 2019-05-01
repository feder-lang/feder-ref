### Declaration and definition

> *stmt* := **func** *func-caps*? *templ-decl*? *func-def-name* *params*? *newline* *body* **;**\
> | **func** *func-caps*? *templ-decl*? *func-decl-name* *params*? **;**\
> | **func** *func-caps*? *templ-decl*? *func-def-name* *params*? *return-type* *newline* *return-body* **;**\
> | **func** *func-caps*? *templ-decl*? *func-decl-name* *params*? *return-type* **;**

> *expr* := **func** *func-caps*? **_** *params*? *newline* *body* **;**\
> | **func** *func-caps* **_** *params*? *return-type* *newline* *return-body* **;**\
> *return-type* := **:** *expr0*

> *func-caps* := **@** *caps*

Where: *expr0* is the return-type.

> *params* := **(** *params-tuple* **)**\
> *params-tuple* := *param* | *param* **,** *params-tuple*\
> *param* := *param-vardecl* *guard*?\
> *param-vardecl* := *vardecl* | *idcalltype*\
> *func-def-name* := *idcall*? *operator* | *idcall*\
> *func-decl-name* := *operator* | *id*

Functions support ad-hoc polymorphism. Functions with the same name mustn't be
declared in the semantic (e.g. traits, classes), if they have the same
parameters.

Example:

```
func helloWorld
  io.println("Hello, World!")
;

helloWorld()

func@Safe safeHelloWorld
  io.println("Hello, World!")
;

safeHelloWorld()

func@Safe mul2(x : int32) : int32
  return x + x
;

io.println(mul2(4))
```
