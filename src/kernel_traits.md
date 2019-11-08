## Traits

Build-in traits:

```
mod std
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
  trait{T,R} Field : Addition{T,R}, Subtraction{T,R},
                     Multiplication{T,R}, Division{T,R}
  ;

  // operator [x]
  trait{T, R} Map
    func at(index: T): R;
  ;

  trait{T} Array : Map{uptr, T}
    // Access element index (start couting from 0)
	// panic if index > length()
    func at(uptr index): T;
	// How many elements can be accessed with func []
	func length: uptr ;
  ;
;
```
