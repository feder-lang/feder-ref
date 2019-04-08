### Do

> *stmt* := **do** *newline* *body* **;** **for** *expr1*\
> | **do** *stmt2* *newline* *body* **;** **for** *expr1*\
> | **do** *stmt0* **;** *stmt2* *newline* *body* **;** **for** *expr1*

where *stmt0* is the initialization, *expr1* the continuation condition and
*stmt2* the iteration step. *expr1* must evaluate to a
[bool](./kernel_bool.md)-value. Executed in the following order:

1) Executed *body* and jump to 2.
2) Check condition, if **True** do 1 otherwise 3.
3) Jump below loop.
