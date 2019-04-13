### Declaration and definition

> *stmt* := **func** *templ-decl*? *func-def-name* *params*? *newline* *body* **;**\
> | **Func** *templ-decl*? *func-def-name* *params*? *newline* *body* **;**\
> | **func** *templ-decl*? *func-decl-name* *params*? **;**\
> | **Func** *templ-decl*? *func-decl-name* *params*? **;**\
> | **func** *templ-decl*? *func-def-name* *params*? *return-type* *newline* *return-body* **;**\
> | **Func** *templ-decl*? *func-def-name* *params*? *return-type* *newline* *return-body* **;**\
> | **func** *templ-decl*? *func-decl-name* *params*? *return-type* **;**\
> | **Func** *templ-decl*? *func-decl-name* *params*? *return-type* **;**

> *expr* := **func** **_** *params*? *newline* *body* **;**\
> | **func** **_** *params*? *return-type* *newline* *return-body* **;**\
> *return-type* := **:** *expr0*

Where: *expr0* is the return-type.

> *params* := **(** *params-tuple* **)**\
> *params-tuple* := *param* | *param* **,** *params-tuple*\
> *param* := *param-vardecl* *guard*?\
> *param-vardecl* := *vardecl* | *idcalltype*\
> *func-def-name* := *idcall*? *operator* | *idcall*\
> *func-decl-name* := *operator* | *id*
