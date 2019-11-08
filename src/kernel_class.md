## Classes

Classes implemented into the kernel:

```
mod std
    class{Type} Box(Var: Type)
        func * =
            Var
        ;
    ;
    
    class{Type} MutBox(var: Type)
        func * =
            var
        ;
    ;

    class NativeString(_chars: Array{char}, _hash,: u8)
    ;

    class trait NativeString : Hash{u8}
        func hash(This) =
            _hash
        ;
    ;

    class trait NativeString : Array{char}
        func at(This, index: uptr): T =
            _chars[index]
        ;

        func length(This) =
            _chars.length()
        ;
    ;
;
```
