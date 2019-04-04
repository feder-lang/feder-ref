## Operator expressions

Expression without the letters 'a' or 'b' are binary operators at default.
Associativity is either 'l' (=left) or 'r' (=right). An operation can be constant
(='y'), not-constant (='n') or cannot be specified (='-'). The latter are
operations, which can't be used as functions.

| Operator     | Precedence | Associativity | Description               | Constant |
| :---:        | :---:      | :---:         | :---                      | :--:     |
| ,            | 1          | l             | Type-Constructor, Comma   | -        |
| :=           | 2          | r             | Auto-define               | -        |
| =            | 3          | r             | Assignments               | n        |
| &= \|= ^=    |            |               |                           | n        |
| += -=        |            |               |                           |          |
| \*= /=       |            |               |                           |          |
| %=           |            |               |                           |          |
| \<\<= \>\>=  |            |               |                           |          |
| =\>          |            | l             | Implies                   | -        |
| \|\|         | 4          | l             | Logical or                | y        |
| &&           | 5          | l             | Logical and               | y        |
| \|           | 6          | l             | Bitwise or                | y        |
| ^            | 7          | l             | Bitwise xor               | y        |
| &            | 8          | l             | Bitwise and               | y        |
| == !=        | 9          | l             | Pointer Comparison        | -        |
| ===          |            |               | Value comparison          | y        |
| \< \<=       | 10         | l             | Value comparison          | y        |
| \> \>=       |            |               |                           |          |
| \>\> \<\<    | 11         |               | Bitshift (right,left)     | y        |
| a+b a-b      | 12         |               | Arithmetic                | y        |
| a\*b a/b a%b | 13         | l             | Arithmetic                | y        |
| :: :?        | 14         | l             | Cast, Check cast          | -        |
| :            |            | r             | Declaration               | -        |
| ++a --a      | 15         | r             | Increment, Decrement      | n        |
| +a -a        |            |               | Positive, Negative        | y        |
| \*a          |            |               | Dereference               | depends  |
| ! ~          |            |               | Logical, bitwise not      | y        |
| .a           |            |               | This member access        | -        |
| &a           |            |               | Cast to R-Value           | -        |
| safe a       |            |               | Safe operation            | -        |
| a++ a--      | 16         | l             | Increment, Decrement      | n        |
| a()          |            |               | Function call             | -        |
| a[]          |            |               | Index access              | depends  |
| a{}          |            |               | Template                  | -        |
| a.a          | 17         | l             | Member access             | -        |
| ->           |            |               | Deref. member access      | depends  |

depends: If all returned types are constant, the function is also constant.

All operators except assignments, declaration and auto-define are part of
*expr*.  Assignments, declarations and function-calls are part of *stmt*.
