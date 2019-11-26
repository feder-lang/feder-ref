# Expressions

This chapter specifies the syntax and semantics.

## Notation

Non-terminals are written *italic* and literal terminals are written in
**bold** style.  Numbers in *terminals* are used as indices. The syntax is
defined with the BNF with operator-precedence and expressions are defined with
the operator **:=**. *Z* represents notation for *no-characters*.

## Ignored characters

Between every expression can be space (vertical,horizontal tabulator and the
space character). In case *space* must be used, it the *space* expression will
be used.

Characters between '//' and end-of-line will be ignored, including '//' and
end-ofline. Also characters between '/\*' and '\*/' will be ignored, including
'/\*' and '\*/'.  These ignored characters are called *comments*. Where a comment
started with '//' will be interpreted as an end-of-line/*newline* and a comment
started with '/\*' as *space*.

## Library name

The optional first expression of an *program* is *progname*. This specifies
where all top-level public semantics in the file should be added to.
if *progname* is not used, the *program*'s semantics won't be visible to other
files.

## Syntax specification

The starting symbol is *program*. The *terminals* where defined in
the chapter [Lexical Elements](./lexical.md).

> *int* := [Integers](./lex_intergers.md)\
> *float* := [Floating-point numbers](./lex_floats.md)\
> *num*   := *int* | *float*\
> *str*   := [Strings](./lex_strings.md)\
> *char*  := [Characters](./lex_chars.md)\
> *literal*  := *num* | *str* | *char*\
> *id* := [Identifiers](./lex_identifiers.md)\
> *EOF* := No characters available\
> *EOL* := *line-feed* *carriage-return*
> | *carriage-return* *line-feed* \
> | *carriage-return* | *line-feed* \
> | Comment starting with *//*\
> *newline* := *EOL* | *EOL* *newline*

```
object(int).
object(float).
object(str).
typename("std.Const<std.String>", str).
object(char).
typename("std.u8", char).
```

> *idcall* := *id* | *id* **.** *idcall*\
> *idcalls* := *idcall* | **(** *idcall* **,** *idcallm* **)**\
> *idcallm* := *idcall* | *idcall* **,** *idcallm*

> *program* := *progname* *newline* *program-body*
> | *progname* *EOF* \
> | *program-body* *EOF* | *EOF* \
> *progname* := **use** **module** *id*

General program:

> *program-body* := *def* *newline* | *def* *EOF*
> | *def* *newline* *program-body*\
> | *use* *newline* | *use* *EOF* | *use* *newline* *program-body*\
> *def* := *func* | *trait* | *class* | *traitimpl*
> | *enum* | *module* | *vardef* | *capsdef*
> *exprdef* := *func* | *trait* | *class* | *traitimpl*
> | *enum* | *capsdef*

[Use](./expr_use.md):
> *use* := **use** *idcall* | **use** *idcall* **.** \*

[Templates](./expr_templs.md):

> *template* :=  **{** *templdecls* **}** \
> *templdecls* := *templdecl* | *templdecl* **,** *templdecls* \
> *templdecl* := *templidcall* | *id* **:** *templidcall* \
> *templidcalls* := *templidcall* | *templidcall* **,** *templidcalls* 
> | *templidcall* **,** *newline* *templidcalls* \
> *templidcall* := *idcall* | *idcall* *template*

```
templatetype(X) :- trait(ctx, X).
templatetype(X) :- typename("std.i8", X).
templatetype(X) :- typename("std.i16", X).
templatetype(X) :- typename("std.i32", X).
templatetype(X) :- typename("std.i64", X).
templatetype(X) :- typename("std.u8", X).
templatetype(X) :- typename("std.u16", X).
templatetype(X) :- typename("std.u32", X).
templatetype(X) :- typename("std.u64", X).
type(ctx, id) :- templatedecl(ctx, id, templidcall), templatetype(ctx, templidcall).
```

[Functions](./expr_fn.md):

> *func* := **func** *funcdecl* *newline* **;**
> | **func** *funcdecl* **=**  *expr* *newline* \
> | **func** *funcdecl* *newline* *funcbody* **;**\
> | **func** *funcdecl* **:** *returntype* *newline* *retfuncbody* **;**\
> | **func** *funcdecl* **:** *newline* *retfuncbody* **;**\
> | *funcnb*\
> *funcnb* := **func** *funcdecl* **;**
> | **func** *funcdecl* **:** *returntype* **;**\
> *funcdecl* := *template* *funcdeclx* | *space* *funcdeclx* \
> *funcdeclx* := *id* | *id* **(** *funcvars* **)**\
> *funcvars* := *funcvar* | *funcvar* **,** *funcvars*\
> *funcvar* := *vardecl* | *vardecl* *guard* \
> *guard* := **|** *expr0* | **\|** *expr0* **=** *expr1*\
> *returntype* := *templidcall* \| *vardecl* \
> *returntypetuple* := **(** *returntuplex* **)** \
> *returntuplex* := *returntupleunit*
> \| *returntupleunit* **,** *returntuplex*\
> *returntupleunit* := *templidcall* \| *id* : *templidcall* \| *func*
> \| *functype*\
> *funcbody* := *stmt* \| *stmt* *newline* *funcbody*\
> *retfuncbody* := *funcbody* **return** *expr* *newline* \
> *functype* := **func** **type** | **func** **type** **:** *return-type*
> | **func** **type** **(** *funcvars* **)**
> | **func** **type** **(** *funcvars* **)** **:** *return-type*

> *clfunc* := **func** *clfuncdecl* *newline* **;**\
> | **func** *clfuncdecl* **:** *returntype* *newline* *retfuncbody* **;**\
> | **func** *clfuncdecl* **:** *newline* *retfuncbody* **;**
> | **func** *clfuncdecl* **=** *newline* *expr* **;** \
> | **func** *clfuncdecl* **:** *returntype* **=** *newline* *expr* **;** \
> | *clfuncnb*\
> *clfuncnb* := **func** *clfuncdecl* **;**
> | **func** *clfuncdecl* **;** *returntype* **;**\
> *clfuncdecl* := *template* *clfuncdeclx* | *space* *clfuncdeclx*\
> *clfuncdeclx* := *id* **(** *funcvars*  **)**

```
object(X) :- function(X).
function([ctx.]id) :- func(
```

[Lambdas](./expr_lambdas.md):

> *lambda* := **lambda** **(** *vardecl* **)** *newline* *retfuncbody* **;**\
> | **lamda** **(** *vardelcs* **)** *newline* *funcbody* **;**\
> | **lambda** *newline* *retfuncbody* **;**\
> | **lamda** *newline* *funcbody* **;**\
> | **lambda** **=** *expr*
> | **lambda** **(** *vardecl* **)** **=** *expr*

[Traits](./expr_traits.md):

> *trait* := **trait** *traitdecl* *newline* *traitbody* **;**\
> | **trait** *traitdecl* *newline* **;**
> *traitdecl* := *id* | *id* **:** *templidcalls*\
> *traitbody* := *clfuncnb* | *clfuncnb* *newline* *traitbody*

[Classes](./expr_classes.md):

> *class* := **class** *classdecl* *newline* *classbody* **;**\
> | **class** *classdecl* *classcons* *newline* *classbody* **;**\
> *classdecl* := *space* *id* | *template* *id*\
> | *space* *id* **:** *templidcalls* | *template* *id* **:** *templidcalls*\
> *classcons* := **(** *vardecl* **)** \
> *classbody* := *classunit* | *classunit* *newline* *classbody*\
> *classunit* := *vardecl* | *caps* *vardecl* | *clfunc* | *caps* *clfunc*

> *traitimpl* := **class** *space* **trait** *traitimpldecl* *newline* *traitimplbody* **;**\
> *traitimpldecl* := *space* *idcall* **:** *templidcall*
> | *template* *idcall* **:** *templidcall*\
> *traitimplbody* := *clfuncnb* | *clfuncnb* *newline* *clfuncnb*

[Enumerations](./expr_enums.md):

> *enum* := **enum** *enumdecl* *newline* *enumbody* **;**\
> *enumdecl* := *id*\
> *enumbody* := *enumunit* | *enumunit* *newline* *enumbody*\
> *enumunit* := *id* | *id* **(** *templidcalls* **)**

[Modules](./expr_mods.md):

> *module* := **module** *moduledecl* *newline* *program-body*\
> *moduledecl* := *id*

General Expression:

> *expr* := *exprdef*
> | **(** *expr* **)**
> | *biopexpr*  | *unopexpr*
> | *fctl* | *lambda*
> | *expr* **(** *expr* **)**
> | *expr* **[** *expr* **]**
> | *array*
> | *safe*
> | *id*
> | *literal*\
> *stmt* := *expr* | *vardecl* | *vardef* | *stmt* **;** *stmt*

Variable declaration:

> *vardecl* := *vardeclunit* | *vardeclunits* \
> *vardeclunits* := *vardeclunit* | *vardeclunit* **,** *vardeclunits*\
> *vardeclunit* := *id* **:** *templidcall* |  **&** *id* **:** *templidcall*\
> | *id* **:** *functype* | **&** *id* **:** *functype*
> *varids* := *varid* | *varid* **,** *varids*\
> *varid* := *id*\

Variable definition:

> *vardef* := *vardecl* **=** *expr*
> | *vardefid* **:=** *expr*
> | **(** *vardefids* **)** **:=** *expr*\
> *vardefids* := *vardefid* | *vardefid* **,** *vardefids*\
> *vardefid* := **&** *id* | *id*

[Arrays](./expr_arrays.md):

> *array* := *arraylit* | *arraycpy* | *arrayfor* \
> *arraylit* := **[** *expr0* **,** *expr1* **]**\
> *arraycpy* := **[** *expr0* *;* *expr1* **]**\
> *arrayempty* :=  **[** *expr* **]**\
> *arrayfor* := **[** **for** *id* **:** *expr0* *newline* *retfuncbody* **]**

[Capabilities](./expr_caps.md):

> *caps* := **#** *capid* *newline* | **#** *capid* *newline* *caps*\
> *capid* := **!** *capsensure* | **Unused** | **Inline** | **Constant** \
> *require* := **requires** *space* *ensurecond*
> | **ensures** *space* *ensurecond*
> | **ensures** *space* *ensurecond0* **=>** *ensurecond1*\
> *capsdef* := *caps* *func* | *caps* *class* | *caps* *enum* | *caps* *vardef*

Control-flow expressions:

> *fctl* := *cond* | *loop*\
> *cond* := *if* | *match* | *ensure*\
> *loop* := *for* | *do*

If expressions:

> *if* := *ifbase* *else* **;** | *ifbase* **;**\
> *ifbase* := **if** *space* *expr* *newline* *funcbody* *newline*\
> \| **if** *space* *expr* *newline* *funcbody* *newline* *loopctl* *newline*\
> \| **if** *space* *expr* *newline* *retfuncbody* *newline*\
> *else* := *elsebase* \| *else* *elsebase*\
> *elsebase* := **else** *space* *expr* *newline* *funcbody* *newline*\
> | **else** *space* *expr* *newline* *retfuncbody* *newline*

[Ensure expression](./expr_ensure.md):

> *ensure* := *ensureunit* **;** | *ensureunit* **else** *ensure*
> | *ensure* **else** *newline* *funcbody* **;**\
> *ensureunit* := **ensure** *ensurecond* *newline* *funcbody*
> *ensurecond* := *idcall* *ensurecondop* *expr*\
> *ensurecondop* := **==** | **!=** | **~=** | **>** | **>=** | **<** | **<=** | **::**

Match expression:

> *match* := *matchbase* *newline* *matchbody* *newline* *;*\
> *matchbase* := **match** *expr*\
> *matchbody* := *matchcase* | *matchcase* *matchbody*\
> *matchcase* := *matchcasecond* **=>** *funcbody* **;**
> | *matchcasesecond* **=>** *retfuncbody* **;**\
> *matchcasecond* := *matchcasecons* | *matchcasecons* *expr*\
> *matchcasecons* := *idcall* | *idcall* **(** *matchids* **)**\
> *matchids* := *matchid* | *matchid* **,** *matchids*\
> *matchid* := **\_** | *id*

Loop expressions:

> *loopctl* := **break** | **continue**\
> *for* := **for** *newline* *funcbody* **;**\
> | **for** *expr* *newline* *funcbody* **;**|
> | **for** *expr* **;** *expr* *newline* *funcbody* **;**\
> | **for** *expr* **;** *expr* **;** *expr* *newline* *funcbody* **;**\
> *do* *newline* *funcbody* **;** **for** *expr*\
> | *do* *expr* *newline* *funcbody* **;** **for** *expr*\
> | *do* *expr* **;** *expr* *newline* *funcbody* **;** **for** *expr*

Safe expression:

> *safe* := **safe** *templidcall* **(** *expr* **)**\
> | **safe** *arraylit*

[Operators](./expr_ops.md):

> *biopexpr* := *expr0* *biop* *expr1*\
> *unopexpr* :=  *lunop* *expr*\
> *biop* := **+** | **-** | \* | **/** | \*\* | **%** \
> | **\&** | **|** | **^** | **<<** | **>>** \
> | **==** | **!=** | **~=** | **<** | **>** | **<=** | **>=**\
> | **&&** | **||**
> **+=** | **-=** | **\*=** | **/=** | \*= | **%=**\
> | **\&=** | **|=** | **^=** | **<<=** | **>>=** \
> | **<\>**\
> | **=**
> | **.** | **-\>**\ | **,**
> *lunop* := \* | **!** | **null** 
> | **+** | **-** | **++** | **--**
