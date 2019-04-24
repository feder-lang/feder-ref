### Declaration and definition

> *stmt* := **func** *func-caps*? *templ-decl*? *func-def-name* *params*? *newline* *body* **;**\
> | **func** *func-caps*? *templ-decl*? *func-decl-name* *params*? **;**\
> | **func** *func-caps*? *templ-decl*? *func-def-name* *params*? *return-type* *newline* *return-body* **;**\
> | **func** *func-caps*? *templ-decl*? *func-decl-name* *params*? *return-type* **;**

> *expr* := **func** *func-caps* **_** *params*? *newline* *body* **;**\
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
