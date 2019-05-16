## Tuples

Every tuple supports two operations (*expr0* and *expr1* are tuples filled with
defined variables):

- *expr0* **==** *expr1*: Only possible if *expr0* has exactly the same amount
  of types as *expr1*. Also every *i*th-type in *expr0* must be exactly the
  same as the *i*th-type in *expr1*. Returns **True**, if every direct *i*th-value in
  *expr0* is the same as the direct *i*th-value in *expr1* (checked with **==**),
  otherwise **False**.

- *expr0* **!=** *expr1*: Only possible if *expr0* has exactly the same amount
  of types as *expr1*. Also every *i*th-type in *expr0* must be exactly the
  same as the *i*th-type in *expr1*. Returns **False**, if every direct *i*th-value in
  *expr0* is the same as the direct *i*th-value in *expr1* (checked with **==**),
  otherwise **True**.
