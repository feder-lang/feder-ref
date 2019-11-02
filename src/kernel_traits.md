## Traits

Build-in traits:

```
mod std
  // the following traits allow a program to use operators with user
  // defined types

  // binary operator '+'
  trait{T,R} Addition
    func add(T): R;
  ;
  // binary operator '-'
  trait{T,R} Subtraction
    func sub(T): R;
  ;
  // binary operator '*'
  trait{T,R} Multiplication
    func mul(T): R;
  ;
  // binary operator '/'
  trait{T,R} Division
    func div(T): R;
  ;
  // sum '+', '-', '*' and '/'
  trait{T,R} Field : Addition{T,R}, Subtraction{T,R},
                     Multiplication{T,R}, Division{T,R}
  ;

  trait{T} Array
    // Access element index (start couting from 0)
	// panic if index > length()
    func [] (uintptr index)
	// How many elements can be accessed with func []
	func length : uintptr ;
  ;
;
```
