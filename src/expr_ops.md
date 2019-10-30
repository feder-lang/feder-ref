## Operators

The less precedence an operator has, the less it binds.

Operator associativity:
- **l**: Operator is left associative
- **r**: Operator is right associative

| Operator | Precedence | Associativity | Description                         |
| :---:    | :---:      | :---:         | :---                                |
| ,        | 1          | l             | Comma, Tuple/argument separator     |
| :=       | 2          | r             | Declaring assignment                |
| &= ^=    | 3          | r             | On-object operation                 | 
| \|=      | 3          | r             | On-object operation                 |
| \<\<=    | 3          | r             | On-object operation                 |
| \>\>=    | 3          | r             | On-object operation                 |
| %=       | 3          | r             | On-object operation                 |
| /= *=    | 3          | r             | On-object operation                 |
| += -=    | 3          | r             | On-object operation                 |
| =        | 3          | r             | Variable  assignment                |
| null a   | 4          | r             | Make empty, returns **()**          |
| \|\|     | 5          | l             | Lazy-logical or                     |
| &&       | 6          | l             | Lazy-logical and                    |
| <>       | 7          | l             | Argument binding                    |
| \|       | 8          | l             | Bitwise or                          |
| ^        | 9          | l             | Bitwise xor                         |
| &        | 10         | l             | Bitwise and                         |
| == !=    | 11         | l             | Value equaltity                     |
| \< \<=   | 12         | l             | Less, Minimum                       |
| \> \>=   | 12         | l             | Greater, Maximum                    |
| \>\> \<\< | 13        | l             | Bitwise right/left shift            |
| a+b a-b  | 14         | l             | Addition, substraction              |
| a%b      | 14         | l             | Remainder                           |
| a*b a/b  | 15         | l             | Multiplication, Division            |
| :        | 16         | r             | Variable declaration                |
| ++a --a  | 17         | r             | Increment, Decrement                |
| +a   -a  | 17         | r             | Positive,Negative                   |
| ! ~      | 17         | r             | Logical not, Bitwise not            |
| *a       | 17         | r             | "Dereference"                       |
