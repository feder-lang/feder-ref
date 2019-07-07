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
| \|       | 6          | l             | Bitwise or                          |
| ^        | 7          | l             | Bitwise xor                         |
| &        | 8          | l             | Bitwise and                         |
| == !=    | 9          | l             | Value equaltity                     |
| \< \<=   | 10         | l             | Less, Minimum                       |
| \> \>=   | 10         | l             | Greater, Maximum                    |
| \>\> \<\< | 11        | l             | Bitwise right/left shift            |
| a+b a-b  | 12         | l             | Addition, substraction              |
| a%b      | 12         | l             | Remainder                           |
| a*b a/b  | 13         | l             | Multiplication, Division            |
| :        | 14         | r             | Variable declaration                |
| ++a --a  | 15         | r             | Increment, Decrement                |
| +a   -a  | 15         | r             | Positive,Negative                   |
| ! ~      | 15         | r             | Logical not, Bitwise not            |
| safe a   | 15         | r             | Safe allocation                     |
| mut a    | 15         | r             | Mutable variable                    |
| sizeof a | 15         | r             | Sizeof type                         |
| *a       | 15         | r             | "Dereference"                       |
