## Syntax Notation

**Literals** are written in bold font and *non-terminals* in italic font. Numbers
used in non-terminals are only there to differ them from the same non-terminals
without the digits.

Examples:

> *expr0* **-** *expr1*

*expr0* and *expr1* refer to the same non-terminal *expr* but can be
distinguished from each other.

> *expr0* **+** *expr1*

is an non-terminal, which starts with an expression, then expects an **+**
and then expects an expression again.

---

> *expr0* | *expr1*

*expr0* or *expr1* match.

---

> *expr* := *expr0*  
> *expr* := *expr1*

is the same as

> *expr* := *expr0* | *expr1*

---

> *expr*?

*expr* is optional.
