### For

> *stmt* := **for** *expr1* *newline* *body* **;**\
> | **for** *expr1* **;** *stmt2* *newline* *body* **;**\
> | **for** *stmt0* **;** *expr1* **;** *stmt2* *newline* *body* **;**

where *stmt0* is the initialization, *expr1* the continuation condition and
*stmt2* the iteration step. *expr1* must evaluate to a
[bool](./kernel_bool.md)-value. Executed in the following order:

1) Check condition, if **True** do 2 otherwise 3.
2) Executed *body* and jump to 1.
3) Jump below loop.
