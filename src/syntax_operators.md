## Operator expressions

Expression without the letters 'a' or 'b' are binary operators at default.
Associativity is either 'l' (=left) or 'r' (=right). An operation can be constant
(='y'), not-constant (='n') or cannot be specified (='-'). The latter are
operations, which can't be used as functions.

| Operator     | Precedence | Associativity | Description               | Constant | Statement |
| :---:        | :---:      | :---:         | :---                      | :---:    | :---:     |
| ,            | 1          | l             | Type-Constructor, Comma   | -        | n         | 
| :=           | 2          | r             | Auto-define               | -        | y         |
| =            | 3          | r             | Assignments               | -        | y         |
| &= \|= ^=    |            |               |                           | n        | y         |
| += -=        |            |               |                           |          |           |
| \*= /=       |            |               |                           |          |           |
| %=           |            |               |                           |          |           |
| \<\<= \>\>=  |            |               |                           |          |           |
| =\>          |            | l             | Implies                   | -        | n         |
| \|\|         | 4          | l             | Logical or                | y        | n         |
| &&           | 5          | l             | Logical and               | y        | n         |
| \|           | 6          | l             | Bitwise or                | y        | n         |
| ^            | 7          | l             | Bitwise xor               | y        | n         |
| &            | 8          | l             | Bitwise and               | y        | n         |
| == !=        | 9          | l             | Pointer Comparison        | -        | n         |
| ===          |            |               | Value comparison          | y        | n         |
| \< \<=       | 10         | l             | Value comparison          | y        | n         |
| \> \>=       |            |               |                           |          | n         |
| \>\> \<\<    | 11         |               | Bitshift (right,left)     | y        | n         |
| a+b a-b      | 12         |               | Arithmetic                | y        | n         |
| a\*b a/b a%b | 13         | l             | Arithmetic                | y        | n         |
| :: :?        | 14         | l             | Cast, Check cast          | -        | n         |
| :            |            | r             | Declaration               | -        | y         |
| ++a --a      | 15         | r             | Increment, Decrement      | n        | y         |
| +a -a        |            |               | Positive, Negative        | y        | n         |
| \*a          |            |               | Dereference               | depends  | n         |
| ! ~          |            |               | Logical, bitwise not      | y        | n         |
| .a           |            |               | This member access        | -        | n         |
| &a           |            |               | Cast to R-Value           | -        | n         |
| safe a       |            |               | Safe operation            | -        | n         |
| a++ a--      | 16         | l             | Increment, Decrement      | n        | y         |
| a()          |            |               | Function call             | -        | y         |
| a[]          |            |               | [Index access](./syntax_arrays.md)               | depends  | n         |
| a{}          |            |               | Template                  | -        | n         |
| a.a          | 17         | l             | [Member access](./syntax_operators_mem.md)       | -        | n         |
| ->           |            |               | Deref. member access      | depends  | n         |

depends: If all returned types are constant, the function is also constant.

All operators except assignments, declaration and auto-define are part of
*expr*.  Assignments, declarations and function-calls are part of *stmt*.
