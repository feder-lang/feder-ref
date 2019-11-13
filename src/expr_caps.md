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

**Requires**:

- Ensure that certain properties are valid. *id* in *ensurecond* can also be
  functions in the same class which only have the class as parameter, next
  to the attributes of the class.

- Function cannot be called if one *ensurecond* is invalid

**Ensures**:

- Ensures that after calling the function, certain properties are valid. The
  *id* **result** can be accessed to ensure that the result behaves in a
  certain way. This also can be conditional on the result, so if the 
  user ensures the *ensurecond0*, *ensurecond1* would automatically be valid.

- The ensurance is not further executed, no further deductions are made.

- The *idcall* in *ensurecond* or *ensurecond1* will be reset before ensurance
  is made. Meaning if ``connected == false`` was ensured and
  ``#!ensure connected == true`` is called, ``connected == false`` will no
  longer be valid.

Example:

```
class Client(_addr : Address)
    _nativeConn : &Option{NativeClientConnection}

    #!requires connected == false
    func _init
        _nativeConn = Option{NativeClientConnection}.None()
    ;

    #!ensures result == false => _nativeConn == Option.None
    #!ensures result == true => _nativeConn == Option.Some
    func connected(This) : bool
        match _nativeConn
            Some(_) => return true ;
            _ => return false ;
        ;
    ;

    #!requires connected == false
    #!ensures result == true => connected == true
    #!ensures result == false => connected == false
    func connect(This) : bool
        _nativeConn = createNativeClientConnection(_addr)
        match _nativeConn
            Some(_) => return true ;
            _ => return false ;
        ;
    ;

    #!requires connected == true
    #!ensures connected == false
    func disconnect
        conn := _nativeConn :: Option.Some
        conn.disconnect()
    ;

    #!requires connected == true
    func send(This, msg : Array{u8})
        conn = _nativeConn :: Option.Some
        conn.send(msg)
    ;

    #!require connected == true
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
        // as ensure connected == true is invalid
        std.io.out << "Connection failure" << std.io.endl
    ;
;
```
