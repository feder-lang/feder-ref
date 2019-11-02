## Lamda functions

In Feder a lambda is a function which can use *variables* declared in previous
*funcbody* scopes. Lambdas are treated as functions with bound arguments, where
the bound arguments are variables, used in the lambda *funcbody*, from previous
*funcbody* scopes. These bound variables must be initialized and will be passed
by using call-by-reference (can also be achieved with **Box{type}**). Variables
in *vardecls* are passed by using call-by-value (like normal function
parameters).

Example:

```
status = "0"
printStatus := lambda 
		null io.out.println("Status: " + status)
	;
printStatus() // prints "Status: 0"
status = "1"
printStatus() // prints "Status: 1"
```
