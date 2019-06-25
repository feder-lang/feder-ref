## Enumerations 

> *stmt* := **enum** *templ-decl*? *id* *newline* *enum-body* **;**\
> *enum-body* := *enum-constructor* | *enum-constructor* *newline* *enum-body*\
> *enum-constructor* := *id* | *id* **(** *idcalltypes* **)**

An enumeration has constructors with different *id*s. Additionally an *id*
can be accompanied by **(** *idcalls* **)**, which allows to store values
of data-types or complex-data-types.

Extracting tuple values without **match** is done with casting. The enumerator
is simply cast to an enumeration constructor. The resulting type will be
an tuple with the types defined by *idcalltypes* in *enum-constructor*.

Example:

```
enum{T} Option
  Just(T)
  None
;

func@Safe{T} printNull(x : Option{T})
  match x
    Just(x) => io.println("Something") ;
	_ => io.println("Nothing") ;
  ;
;

canBeNull := None{int32}()
printNull(canBeNull)
canBeNull := Just(2)
printNull(canBeNull)
```
