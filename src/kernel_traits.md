## Traits

Build-in traits:

```
use module std
// the following traits allow a program to use operators with user
// defined types

// binary operator '+'
trait{T,R} Addition
  func add(rhs: T): R;
;
// binary operator '-'
trait{T,R} Subtraction
  func sub(rhs: T): R;
;
// binary operator '*'
trait{T,R} Multiplication
  func mul(rhs: T): R;
;
// binary operator '/'
trait{T,R} Division
  func div(rhs: T): R;
;
// sum '+', '-', '*' and '/'
// compiler assumes the following is correct:
//   - a + b = b + a
//   - a * b = b * a
//   - a * (b+c) = (a*b) + (a*c)
//   - a * (b-c) = (a*b) - (a*c)
trait{T,R} StdField : Addition{T,R}, Subtraction{T,R},
    Multiplication{T,R}, Division{T,R}
;

// binary operator '~='
trait{R, T} ComparisonEquals
  func equals(T): R;
;

// binary operator <, >
// operator a > b is replaced by b < a
trait{R, T} Comparison : ComparisonEquals{R, T}
  func lesserThan(T): R;
  func less
;

// operator [x]
trait{T, R} Map
  func at(index: T): R;
;

trait{T} Array : Map{uptr, T}
  // Access element index (start couting from 0)
  // panic if index > length()
  func at(index: uptr): T;
  // How many elements can be accessed with func []
  func length: uptr ;
;

trait{T: ComparisonEquals{bool, T}} Hash
  func hash: T
;
```
