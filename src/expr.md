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
end-ofline. Also characters between '/*' and '*/' will be ignored, including
'/*' and '*/'.  These ignored characters are called *comments*. Where a comment
started with '//' will be interpreted as an end-of-line/*newline* and a comment
started with '/*' as *space*.

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

> *strs* := *str* | **(** *strm* **)**\
> *strm* := *str* | *str* **,** *strm*\
> *idcall* := *id* | *id* **.** *idcall*\
> *idcalls* := *idcall* | **(** *idcall* **,** *idcallm* **)**\
> *idcallm* := *idcall* | *idcall* **,** *idcallm*

> *program* := externs program-body *EOF* | program-body *EOF* | *EOF*

External dependencies:

> *externs*  := includes import | includes | imports\
> *includes* := *include* | *include* *newline* *includes*\
> *include* := **include** *strs*\
> *imports*  := *import* | *import* *newline* *imports*\
> *import* := **import** *idcalls*

General program:

> *program-body* := *def* | *def* *newline* *program-body*\
> *def* := *func* | *trait* | *class* | *traitimpl*
> | *enum* | *module* | *vardef*

[Templates](./expr_templs.md):

> *template* :=  **{** *templdecls* **}** \
> *templdecls* := *templdecl* | *templdecl* **,** *templdecls* \
> *templdecl* := *id* | *id* **:** *templidcall* \
> *templidcalls* := *templidcall* | *templidcall* **,** *templidcalls* 
> | *templidcall* **,** *newline* *templidcalls* \
> *templidcall* := *idcall* | *idcall* *template*

[Functions](./expr_fn.md):

> *func* := **func** *funcdecl* *funcbody* *newline* **;** \
> | **func** *funcdecl* **:** *returntype* *newline* *retfuncbody* **;**\
> | **func** *funcdecl* **:** *newline* *retfuncbody*\
> | *funcnb*\
> *funcnb* := **func** *funcdecl* **;**
> | **func** *funcdecl* **:** *returntype* **;**\
> *funcdecl* := *template* *funcdeclx* | *space* *funcdeclx*
> | *template* *caps* *funcdeclx* | *caps* *space* *funcdeclx*\
> *funcdeclx* := *idcall* | *idcall* **(** *funcvars* **)**\
> *funcvars* := *funcvar* | *funcvar* *funcvars*\
> *funcvar* := *vardecl* | *vardecl* *guard*\
> *guard* := **|** *expr0* | **|* *expr0* **=>** *expr1*.
> *returntype* := *templidcall* | *vardecltuple* \
> *returntypetuple* := **(** *returntuplex* **)** \
> *returntuplex* := *returntupleunit*
> \| *returntupleunit* **,** *returntuplex*\
> *returntupleunit* := *templidcall* | *id* : *templidcall* | *func*
>                      | *functype*\
> *funcbody* := *expr* | *expr* *newline* *funcbody*\
> *retfuncbody* := *funcbody* **return** *expr* *newline* \| *funcbody*
> *functype* := **func** | **func** **:** *return-type*
> | **func** **(** *vardecls* **)**
> | **func** **(** *vardecls* **)** **:** *return-type*

> *clfunc* := **func** *clfuncdecl* *newline* **;**\
> | **func** *clfuncdecl* **:** *returntype* *newline* *retfuncbody* **;**\
> | **func** *clfuncdecl* **:** *newline* *retfuncbody* **;**
> | *clfuncnb*\
> *clfuncnb* := **func** *clfuncdecl* **;**
> | **func** *clfuncdecl* **;** *returntype* **;**\
> *clfuncdecl* := *template* *clfuncdeclx* | *space* *clfuncdeclx*\
> | *template* *caps* *clfuncdeclx* | *caps* *space* *clfuncdeclx*\
> *this* := **This** | **this**\
> *clfuncdeclx* := *id* **(** *this* **)**
> | *id* **(** *this* **,** *funcvars* **)**\

[Lambdas](./expr_fn.md):

> *lambda* := **(** *vardecls* **)** **->** *retfuncbody* **;**
> | *vardecl* **->** *retfuncbody* **;**
> | **(** **)** **->** *retfuncbody* **;**

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
> *classcons* := **(** *vardecls* **)** \
> *classbody* := *classunit* | *classunit* *newline* *classbody*\
> *classunit* := *vardecl* | *clfunc*

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

> *expr* := *def* | *vardecl*
> | **(** *expr* **)**
> | *biopexpr*  | *unopexpr*
> | *fctl* | *lambda*

Variable declaration:

> *vardecl* := *vardeclunit* | **(** *vardeclunits* **)**\
> *vardeclunits* := *vardeclunit* | *vardeclunit* **,** *vardeclunits*\
> *vardeclunit* := *id* **:** *templidcall*
> | **mut** *space* *id* **:** *templidcall*\
> *varids* := *varid* | *varid* **,** *varids*\
> *varid* := *id* | **mut** *space* *id*

Variable definition:

> *vardef* := *vardecl* **=** *expr* | *varid* **:=** *expr*
> | **(** *varids* **)** **:=** expr

Capabilities:

> *caps* := *cap* | *cap* *caps*\
> *cap* := **@** *capid*\
> *capid* := **Var** | **Label**

Flow-control expressions:

> *fctl* := *cond* | *loop*\
> *cond* := *if* | *match*\
> *loop* := *for* | *do*

If expressions:

> *if* := *ifbase* *else* **;** | *ifbase* **;**\
> *ifbase* := **if** *space* *expr* *newline* *funcbody* *newline*\
> \| **if** *space* *expr* *newline* *funcbody* *newline* *loopctl* *newline*\
> \| **if** *space* *expr* *newline* *retfuncbody* *newline*\
> *else* := *elsebase* \| *else* *elsebase*\
> *elsebase* := **else** *space* *expr* *newline* *funcbody* *newline*\
> | **else** *space* *expr* *newline* *retfuncbody* *newline*

Match expression:

> *match* := *matchbase* *newline* *matchbody* *newline* *;*\
> *matchbase* := **match** *expr*\
> *matchbody* := *matchcase* | *matchcase* *matchbody*\
> *matchcase* := *matchcasecond* **=>** *funcbody* **;**
> | *matchcasesecond* **=>** *retfuncbody* **;**\
> *matchcasecond* := *matchcasecons* | *matchcasecons* *expr*\
> *matchcasecons* := *idcall* | *idcall* **(** *matchids* **)**\
> *matchids* := *matchid* | *matchid* **,** *matchids*\
> *matchid* := **_** | *id*

Loop expressions:

> *loopctl* := **break** | **continue**
> *for* := **for** *newline* *funcbody* **;**\
> | **for** *expr* *newline* *funcbody* **;**|
> | **for** *expr* **;** *expr* *newline* *funcbody* **;**\
> | **for** *expr* **;** *expr* **;** *expr* *newline* *funcbody* **;**\
> *do* *newline* *funcbody* **;** **for** *expr*\
> | *do* *expr* *newline* *funcbody* **;** **for** *expr*\
> | *do* *expr* **;** *expr* *newline* *funcbody* **;** **for** *expr*

Operators:

> *biopexpr* := *expr0* *biop* *expr1*\
> *unopexpr* := *expr* *runop*\
> *biop* := **+** | **-** | **\*** | **/** | **\*\*** | **%** \
> | **\&** | **|** | **^** | **<<** | **>>** \
> | **==** | **!=** | **<** | **>** | **<=** | **>=**\
> | **&&** | **||**
> **+=** | **-=** | **\*=** | **/=** | **\*\*=** | **%=**\
> | **\&=** | **|=** | **^=** | **<<=** | **>>=** \
> | **=**
> | **<>**\
> *runop* := **\*** | **!** | **safe** | **mut** | **sizeof** | **null** 
> | **+** | **-** | **++** | **--**
