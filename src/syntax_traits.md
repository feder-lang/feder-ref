## Traits

> *stmt* := **trait** *templ-decl*? *id* *implements*? *newline* *trait-body* **;**\
> *implements* := **:** *idcalls*\
> *trait-body* := *trait-func* | *trait-func* *newline* *trait-body*\
> *trait-func* := **Func** *func-decl-name* *params*? *return-type*? **;**

Where: *implements* are traits, the trait implements, too. A trait only has
declared virtual functions.

In *implements* a trait must only be referenced one time directly.

```
trait Printer
	Func printuint8(x : uint8) ;
	Func printint8(x : int8) ;
;
```
