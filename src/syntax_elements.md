## Basic non-terminals

Some basic non-terminals.

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

> *idcall* := *id* | *id* **.** *idcall*
