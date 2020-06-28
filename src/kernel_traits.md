## Traits

Build-in traits:

```
use module std
// the following traits allow a program to use operators with user
// defined types

// binary operator '+'
trait{T,R} Addition
  func Add(rhs: T): R;
;
// binary operator '-'
trait{T,R} Subtraction
  func Sub(rhs: T): R;
;
// binary operator '*'
trait{T,R} Multiplication
  func Mul(rhs: T): R;
;
// binary operator '/'
trait{T,R} Division
  func Div(rhs: T): R;
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
  func Equals(T): R;
;

// binary operator <, >
// operator a > b is replaced by b < a
trait{R, T} Comparison : ComparisonEquals{R, T}
  func LesserThan(T): R;
;

// operator [x]
trait{T, R} Map
  // Expression: *expr0* **[** *expr1* **]**
  // *expr0* is this
  // *expr1* is index
  func At(index: T): R;

  // Expression: *expr0* **[** *expr1* **]** = *expr2*
  // *expr0* is this
  // *expr1* is index
  // *expr2* is val
  // Returns val 
  func set(index: T, val: R): R;
;

trait{T} Array : Map{std.uptr, T}
  // Access element index (start couting from 0)
  #!requires index < Length()
  func At(index: uptr): T;

  // How many elements can be accessed with func []
  func Length: uptr ;
;

trait{T} Assignment
	// Expression: **\*** *expr0* = *expr1*
	// Returns val.
	func set(val: T): T;
;

trait{T: ComparisonEquals{bool, T}} Hash
  func Hash: T
;

trait ScopeDestructor
	// Is called one variable, if it's end of scope is reached
	func leaveScope;
;
```
