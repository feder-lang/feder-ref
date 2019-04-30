# bool

Bool(ean) data-type. Values are either the tokens **True** or **False**.

Operators defined on booleans:

- *bool0* **&&** *bool1*: Evaluate *bool0*. If evaluated *bool0* is false,
  return false, otherwise evaluate *bool1* and return evaluated *bool1*.

- *bool0* **||** *bool1*: Evaluate *bool*. If evaluated *bool0* is true, return
  true, otherwise evaluate *bool1* and return evaluated *bool1*.

- **!** *bool0*: Evaluate *bool0*. IF evaluated *bool0* is true, return False,
  otherwise return True.

- *expr0* **==** *expr1*: Return true, if *expr0* and *expr1* are True. Also
  return True, if *expr0* and *expr1* are False. In all othercases False is
  returned.

- *expr0* **!=** *expr1*: Returns the same as \
  **!** **(** *expr0* **==** *expr1* **)**
