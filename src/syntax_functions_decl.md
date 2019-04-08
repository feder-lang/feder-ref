### Declaration and definition

> *stmt* := **func** *func-def-name* *params*? *return-type*? *body* **;**\
> | **Func** *func-def-name* *params*? *return-type*? *body* **;**\
> | **func** *func-decl-name* *params*? *return-type*? **;**\
> | **Func** *func-decl-name* *params*? *return-type*? **;**\
> *expr* := **func** **_** *params*? *return-type*? *body* **;**\
> *return-type* := **:** *expr0*

Where: *expr0* is the return-type.

> *params* := **(** *params-tuple* **)**\
> *params-tuple* := *param* | *param* **,** *params-tuple*\
> *param* := *param-vardecl* *guard*?\
> *param-vardecl* := *vardecl* | *idcalltype*\
> *func-def-name* := *idcall*? *operator* | *idcall*\
> *func-decl-name* := *operator* | *id*
