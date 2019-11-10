# Integers

- i8: 8-bit integer (signed octet)
- u8: 8-bit unsigned integer (unsigned octet)
- i16: 16-bit integer (signed short)
- u16: 16-bit unsigned integer (unsigned short)
- i32: 32-bit integer (unsigned int)
- u32: 32-bit unsigned integer (signed int)
- i64: 64-bit integer (signed quad)
- u64: 64-bit unsigned integer (unsigned quad)
- iptr: Architecture dependent size (signed)
- uptr: Architecture dependent size (unsigned). Used for pointers and size
  of arrays.

More about integers at
[Wikipedia](https://en.wikipedia.org/wiki/Integer_%28computer_science%29).
Every integer-type starting with **u** are unsigned, all others are signed.

Unary operators defined on integers:

- **-** *expr0*: Return *expr0* multiplied by -1. Return-type is the one of
  *expr0*.
- **~** *expr0*: Bitwise inverse of *expr0*. Return-type is the one of *expr0*.

Binary operators defined on integers:

- *expr0* **+** *expr1*: Return sum of *expr0* and *expr1*. *expr0* and *expr1*
  must have the same type. Return-type is the one of *expr0*.
- *expr0* **-** *expr1*: Returns sum of *expr0* and **-** *expr1*. *expr0* and
  *expr1* must have the same type. Return-type is the one of *expr0*.
- *expr0* ** \* ** *expr1*: Returns *expr0* multiplied by *expr1*. *expr0* and
  *expr1* must have the same type. Return-type is the one of *expr0*.
- *expr0* **/** *expr1*: Returns *expr0* divided by *expr1*. *expr0* and
  *expr1* must have the same type. Return-type is the one of *expr0*.
  *expr1* must be ensured not to be equal to 0.

- *expr0* **&** *expr1*: Return bitwise conjunction of *expr0* and *expr1*.
  *expr0* and *expr1* must have the same type. Return-type is the on of
  *expr0*.
- *expr0* **|** *expr1*: Return bitwise inclusive conjunction of *expr0* and
  *expr1*.  *expr0* and *expr1* must have the same type. Return-type is the on
  of *expr0*.  
- *expr0* **^** *expr1*: Return bitwise exclusive conjunction of *expr0* and
  *expr1*.  *expr0* and *expr1* must have the same type. Return-type is the on
  of *expr0*.  

- *expr0* **\<\<** *expr1*. Return number *expr0* shifted *expr1* to the left.
  *expr1* must have the type **uint16**. Return type is the one of *expr0*.
- *expr0* **\>\>** *expr1*. Return number *expr0* shifted *expr1* to the right.
  If *expr0* is a signed-type, the new bits are either 0 (if positive) or 1 (if
  negative).  *expr1* must have the type **uint16**. Return type is the one of
  *expr0*.

- *expr0* **==** *expr1*: Returns True if numbers *expr0* and *expr1* are equal
  (*expr0* - *expr1* is equal to 0), otherwise False.  *expr0* and *expr1* must
  have the same type. Return-type is [bool](./kernel_bool.md).
- *expr0* **!=** *expr1*: Returns False if numbers *expr0* and *expr1* are
  equal (*expr0* - *expr1* is not equal to 0), otherwise True. *expr0* and
  *expr1* must have the same type. Return-type is [bool](./kernel_bool.md).

- *expr0* **++**: Post-increment *expr0*. Returns *expr0* and then executes
  *expr0* **+=** **1**.

- *expr0* **--**: Post-decrement *expr0*. Returns *expr0* and then executes
  *expr0* **-=** **1**.

- **++** *expr0*: Pre-increment *expr0*. Executes *expr0* **+=** **1** and then
  returns *expr0*.

- **--** *expr0*: Pre-decrement *expr0*. Executes *expr0* **-=** **1** and then
  returns *expr0*.
