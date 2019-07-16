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
| \|\|     | 4          | l             | Lazy-logical or                     |
| &&       | 5          | l             | Lazy-logical and                    |
| <>       | 6          | l             | Argument binding                    |
| \|       | 7          | l             | Bitwise or                          |
| ^        | 8          | l             | Bitwise xor                         |
| &        | 9          | l             | Bitwise and                         |
| == !=    | 10         | l             | Value equaltity                     |
| \< \<=   | 11         | l             | Less, Minimum                       |
| \> \>=   | 11         | l             | Greater, Maximum                    |
| \>\> \<\< | 12        | l             | Bitwise right/left shift            |
| a+b a-b  | 13         | l             | Addition, substraction              |
| a%b      | 13         | l             | Remainder                           |
| a*b a/b  | 14         | l             | Multiplication, Division            |
| :        | 15         | r             | Variable declaration                |
| ++a --a  | 16         | r             | Increment, Decrement                |
| +a   -a  | 16         | r             | Positive,Negative                   |
| ! ~      | 16         | r             | Logical not, Bitwise not            |
| safe a   | 16         | r             | Safe allocation                     |
| mut a    | 16         | r             | Mutable variable                    |
| sizeof a | 16         | r             | Sizeof type                         |
| *a       | 16         | r             | "Dereference"                       |
