## Basic (non-)terminals

Some basic non-terminals or how certain terminals are referred to.

> *expr* := *id* | *constant*

---

> *newline*

Newline character.

---

> *id*

refers to the lexical token [identifier](./lex_identifiers.md).

---

> *constant*

refers to the lexical tokens [integer](./lex_integers.md),
[floating-point numbers](./lex_floats.md), [characters](./lex_chars.md)
and [strings](./lex_strings.md).

---

> *idcall* := *id* | *id* **.** *idcall*\
> *idcalls* := *idcall* | *idcall* **,** *idcalls*\
> *ids* := *id* | *id* **,** *ids*
> *idcalltype* := *idcall* *arraytypes*?\
> *idcalltypes* := *idcall* *arraytypes*? | *idcall* *arraytypes*? **,** *idcalltypes*

---

> *body* := *stmt* | *stmt* *newline* *body*

---

> *return-body*

where *return-body* is a *body* but the laster expression is either an
[if-expression](./syntax_conditional_if.md), a
[match-expression](./syntax_conditional_match.md) or the body is followed by
'**return** *expr*', where *expr* is the object to return.
