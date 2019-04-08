### If

> *stmt* := *if-stmt*\
> *if-stmt* := **if** *expr* *newline* *body* *else-stmt*? **;**\
> *else-stmt* := **else** **if** *expr* *newline* *body* *else-stmt*?\
> | **else** *newline* *body*

> *expr* := *if-expr*\
> *if-expr* := **if** *expr* *newline* *return-body* *else-expr* **;**\
> *else-expr* := **else** **if** *expr* *newline* *return-body* *else-expr*\
> | **else** *newline* *return-body*

where *expr* evaluates to a [bool](./kernel_bool.md)-value. The first *body* or
*return-body* which previously stated *expr*-condition is *True* will be
executed.  If no *expr* evaluates to *True*, the *return-body* of '**else**
*newline* *return-body*' will be executed in *if-expr*. If no *expr* evaluates
to *True* in *stmt*, the *body* of '**else** *newline* *body*' will be
executed, if the **else**-case it exists.
