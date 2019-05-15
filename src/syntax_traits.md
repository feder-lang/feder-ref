## Traits

> *stmt* := **trait** *templ-decl*? *id* *implements*? *newline* *trait-body* **;**\
> *implements* := **:** *idcalls*\
> *trait-body* := *trait-func* | *trait-func* *newline* *trait-body*\
> *trait-func* := **Func** *func-decl-name* *params*? *return-type*? **;**

Where: *implements* are traits, the trait implements, too. A trait only has
declared virtual functions. A class instance can be casted to a trait instance
implemented by the class. A trait instance can be cast back. Functions mustn't
be private. It is not possible to implement traits, which have functions with
the same, which don't support polymorphism or have the same parameters but
different return types (including functions of the current trait).

*trait-func*s are **members** of the trait.

In *implements* a trait must only be referenced one time directly.

```
trait Printer
	Func printuint8(x : uint8) ;
	Func printint8(x : int8) ;
;

// MyPrinter is a class which implements Printer
// Cast MyPrinter instance to Printer instance
printStream : Printer
printStream = MyPrinter() :: Printer
printStream.printuint8(0x0A)
```
