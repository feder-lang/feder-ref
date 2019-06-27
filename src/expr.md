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
> *idcalls* := *idcall* | **(** *idcallm* **)**\
> *idcallm* := *idcall* | *idcall* **,** *idcallm*

> *program* := externs program-body *EOF* | program-body *EOF* | *EOF*

> *externs*  := includes import | includes | imports\
> *includes* := *include* | *include* *newline* *includes*\
> *include* := **include** *strs*\
> *imports*  := *import* | *import* *newline* *imports*\
> *import* := **import** *idcalls*

> *program-body* := *def* | *def* *newline* *program-body*\
> *def* := *func* | *trait* | *class* | *enum* | *vardef*

> *template* :=  **{** *templdecls* **}**\
> *templdecls := *templdecl* | *templdecl* **,** *templdecls*\
> *templdecl* := *id* | *id* **::** *templidcall*\
> *templidcalls* := *templidcall* | *templidcall* **,** *templidcalls*\
> *templidcall* := *idcall* | *idcall* *template*

> *func* := **func** *funcdecl* *funcbody* *newline* **;**
> | **func** *funcdecl* **:** *return-type* *retfuncbody*\
> *funcdecl* := *template* *funcdeclx* | *space* *funcdeclx*\
> *funcdeclx* := *id* **(** *funcvars* **)**\
> *return-types* := *templidcall* | **(** *return-typem* **)**\
> *return-typem* := *id* **:** *templidcall* | *templidcall*
> | *templidcall* **,** *return-typem*\
> *funcbody* := *expr* | *expr* *newline* *funcbody*\
> *retfuncbody* := *funcbody* **return** *expr* *newline* **;**
> | *funcbody* *expr* **;**

