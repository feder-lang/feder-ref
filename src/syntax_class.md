## Classes

> *stmt* := **class** *templ-decl*? *id* *implements*? *newline* *class-body* **;**\
> *expr* := **class** **_** *implements*? *newline* *class-body* **;**\
> *class-body* := *class-stmt* | *class-stmt* *newline* *class-body*\
> *class-stmt* := **func** *func-decl-name* *params*? *return-type*? *newline* *body* **;**\
> | **Func** *func-decl-name* *params*? *return-type*? *newline* *body* **;**\
> | **func** *func-decl-name* *params*? *return-type*? **;**\
> | **Func** *func-decl-name* *params*? *return-type*? **;**\
> | *id* *return-type*

Class can implement traits, have not-virtual constructor functions, virtual
functions, which implement declared trait-functions and normal functions. All
function can access the variables *this* and *This*. The *this* variable
is passed to a function as instance (if the LHS side of the **.** operator
is an value) or as the first argument (if the LHS side of the **.** operator
is a class-type). Also all class-functions can access all attributes of the
class directly.

Example:

```
class Person
	_name : std.String
	_age : int32

    // Below is a constructor
	func Person(name : std.String, age : int32)
		._name = name
		._age = age
	;

	func printName
		std.io.println(._name)
	;
;

// Create an instant of Person and save it in p0
p0 := Person(std.String("Noone"), -1)

p0.printName()
Person.printName(p0)
```

### this

Function in classes can access the variables called *this* and *This*, where
*this* returns a not-constant value with the same type as the current class
and can only be used in not-constant functions and *This* returns a constant
value with the same type as the current class. The unary prefix operator **.**
automatically selects the most permissive *this* variable. So in a not-constant
class-function **.** is equal to **this.** and in a constant one **.**
is equal to **This.**.

### Constructors

To create a value from a class-type, constructors are used. At default every
class, which doesn't have any custom constructors, has a constructor with no
parameters. Custom constructors are not-virtual functions, which have the
same name as the class or equal to name of the class prefixed with a **_**. The
latter is a private constructor. To construct a value from a class,
a class-type has to be called just like a function. Example:

```
class Person
	_name : std.String
	_age : int32

    // Below is a constructor
	func Person(name : std.String, age : int32)
		._name = name
		._age = age
	;

	func printName
		std.io.println(._name)
	;
;

// Create an instant of Person and save it in p0
p0 := Person(std.String("Noone"), -1)
```

### Implement Traits

All declared functions of the traits (referenced in *implements*) must defined
in the class. A class can be represented as an implemented trait
(polymorphism).
