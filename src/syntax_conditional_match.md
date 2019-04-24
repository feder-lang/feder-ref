### Match

> *expr* := **match** *expr* *newline* *match-expr-body* **;**\
> *match-expr-body* := *match-expr-case* | *match-expr-case* *newline* *match-expr-body*\
> *match-expr-case* := *match-case* **=>** *return-body* **;**\
> *stmt* := **match** *expr* *newline* *match-stmt-body* **;**\
> *match-stmt-body* := *match-stmt-case* | *match-stmt-case* *match-stmt-body*\
> *match-stmt-case* := *match-case* **=>** *body* **;**\
> *match-case* := **_** | *idcall* *match-case-obj*? \
> *match-case-obj* := **(** *ids* **)**

where *expr* must return a *enum*-value. *idcall* must be an enum-constructor
of the type *expr* returned. *match-case-obj* must have an *id* for every
constructor value the *idcall* requires. '**_** **=>** *body* **;**' is the
default case, which is executed if no other case matched.  A *match-expr-body*
must have one default case.

Example:

```
enum{T} Maybe
  Nothing
  Just(T)
;

match Nothing{std.String}()
  Nothing => io.println("Nothing") ;
  Just(x) => io.println(x) ;
;
```
