## Enumerations 

> *stmt* := **enum** *templ-decl*? *id* *newline* *enum-body* **;**\
> *enum-body* := *enum-constructor* | *enum-constructor* *newline* *enum-body*\
> *enum-constructor* := *id* | *id* **(** *idcalltypes* **)**

An enumeration has constructors with different *id*s. Additionally an *id*
can be accompanied by **(** *idcalls* **)**, which allows to store values
of data-types or complex-data-types.
