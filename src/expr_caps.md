## Capabilities

Capabilities can modify how a function is called, implemented or changes
compile time informations about an object.

**Capabilities**:

- **Unused**: Still implement semantic, even if unused

- **Inline**: Function name is removed its own environment (prevents direct
  recursion). Tells compiler to eventually directly implement function
  instead of calling it. Classes are used as tuples, which cannot be casted
  to traits.

- **Constant**: Function can be computed at compile time. Only primitive
  datatypes can be used.

- **Internal**: Semantic is handled by the compiler

**Requires**:

- Ensure that certain properties are valid. *id* in *ensurecond* can also be
  functions in the same class which only have the class as parameter, next
  to the attributes of the class.

- Function cannot be called if one *ensurecond* is invalid

**Ensures**:

Ensurance is a way to express the state of an object during compile-time.
This allows the programmer to detect invalid state at compile-time.

- Ensures that after calling the function, certain properties are valid. The
  *id* **result** can be accessed to ensure that the result behaves in a
  certain way. This also can be conditional on the result, so if the 
  user ensures the *ensurecond0*, *ensurecond1* would automatically be valid.

- Deductions are made based on the implication *ensurecond0* => *ensurecond1*.
  If *ensurecond0* is valid *ensurecond1* is also valid.  Then *ensurecond1* is
  checked if it is *ensurecond1* in an implication.

- The *idcall* in *ensurecond* or *ensurecond1* will be reset before ensurance
  is made. Meaning if ``connected == False`` was ensured and
  ``#!ensure connected == True`` is called, ``connected == False`` will no
  longer be valid.

- When the condition is a binary expression, the left side is the
  a compile-time object and the right side it's state. The compile-time object
  is bound to the runtime-object (object of class, trait, type).
  If it is unary, the expression will be the compile-time object.

- Deductions:
	* x == True => x != False
	* x == False => x != True
	* x => x == True
	* !x => x == False
	* x < y => x != y
	* x > y => x != y
	* x < y, y < z => x < z (This makes x > 0 valid for x > 512)

Example:

```
class Client(_addr : Address)
    _nativeConn : &Option{NativeClientConnection}

    #!requires connected == False
    func _init
        _nativeConn = Option{NativeClientConnection}.None()
    ;

    #!ensures result == False => _nativeConn == Option.None
    #!ensures result == True => _nativeConn == Option.Some
    func connected(This) : bool
        match _nativeConn
            Some(_) => return True ;
            _ => return False ;
        ;
    ;

    #!requires connected == False
    #!ensures result == True => connected == True
    #!ensures result == False => connected == False
    func connect(This) : bool
        _nativeConn = createNativeClientConnection(_addr)
        match _nativeConn
            Some(_) => return True ;
            _ => return False ;
        ;
    ;

    #!requires connected == True
    #!ensures connected == False
    func disconnect
        conn := _nativeConn :: Option.Some
        conn.disconnect()
    ;

    #!requires connected == True
    func send(This, msg : Array{u8})
        conn = _nativeConn :: Option.Some
        conn.send(msg)
    ;

    #!require connected == True
    func receive(This, msg : Array{u8})
        conn = _nativeConn :: Option.Some
        conn.send(msg)
    ;
;

func main
    client := Client(Address("127.0.0.1", 22))
    ensure client.connect()
        std.io.out << "Connected to server" << std.io.endl
        client.send("help the world")
        client.disconnect()
        // client.send, receive no longer callable
    else
        // client.send, receive cannot be called here
        // as ensure connected == True is invalid
        std.io.out << "Connection failure" << std.io.endl
    ;
;
```
