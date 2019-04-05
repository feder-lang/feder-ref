## Traits

> *stmt* := **trait** *id* *implements*? *newline* *trait-body* **;**\
> *implements* := **:** *idcalls*\
> *idcalls* := *idcall* | *idcall* **,** *idcalls*\
> *trait-body* := *trait-func* | *trait-func* *newline* *trait-body*\
> *trait-func* := **Func** *func-decl-name* *params*? *return-type*? **;**

Where: *implements* are traits, the trait implements, too. A trait only has
declared virtual functions.
