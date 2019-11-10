# Floating-point numbers

- f32: IEC-559/IEEE-754 32-bit float-point number (float, in IEEE-754:
  binary32)
- f64: IEC-559/IEEE-754 64-bit float-point number (double, in IEEE-754:
  binary64)

More about floats at [Wikipedia](https://en.wikipedia.org/wiki/IEEE_754).

Unary operators defined on integers:

- **-** *expr0*: Return *expr0* multiplied by -1. Return-type is the one of
  *expr0*.

Binary operators defined on floats:

- *expr0* **+** *expr1*: Return sum of *expr0* and *expr1*. *expr0* and *expr1*
  must have the same type. Return-type is the one of *expr0*.
- *expr0* **-** *expr1*: Returns sum of *expr0* and **-** *expr1*. *expr0* and
  *expr1* must have the same type. Return-type is the one of *expr0*.
- *expr0* ** \* ** *expr1*: Returns *expr0* multiplied by *expr1*. *expr0* and
  *expr1* must have the same type. Return-type is the one of *expr0*.
- *expr0* **/** *expr1*: Returns *expr0* divided by *expr1*. *expr0* and
  *expr1* must have the same type. Return-type is the one of *expr0*.
  The value *expr1* must be ensured to be not 0.0.

- *expr0* **==** *expr1*: Returns True if numbers *expr0* and *expr1* are equal
  (*expr0* - *expr1* is equal to 0), otherwise False.  *expr0* and *expr1* must
  have the same type. Return-type is [bool](./kernel_bool.md).
- *expr0* **!=** *expr1*: Returns False if numbers *expr0* and *expr1* are
  equal (*expr0* - *expr1* is not equal to 0), otherwise True. *expr0* and
  *expr1* must have the same type. Return-type is [bool](./kernel_bool.md).
