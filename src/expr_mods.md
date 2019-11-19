## Modules

Modules separate code by functionality. A module has an own environment and
is added as *id* from *moduledecl* to the parent environment. A module's
*id* must start with an lowercase, alphabetic character.

Libraries are also just modules.

Example:

```
module hello
	func world
		null io.println("Hello, World!")
	;
;

func main
	hello.world() // Prints hello world to standard output
;
```

### Variables

Variables in modules can be either **global**, if the module has only modules
and library as parents otherwise the variable is **local**.

Non-primitive, **global** variables are initialized when *first called*
(lazy-initialization).

Examples:

```
module mymod
	class Person (name : String,
		          age : u8)
		func getName(this : This) =
			name;
		func getAge(this : This) =
			age;
	;

	myglobvalue := 100          // primitive global variable
	me := Person("Someone", 16) // me is not initialized !!!
;

func main
	io.println(mymod.myglobvalue)
	io.println(mymod.me.getName()) // Initialized mymod.me
;
```
