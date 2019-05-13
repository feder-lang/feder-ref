## Casting

> expr := expr **::** expr\
> | expr **:?** expr

With **::** an complex-object is casted to another type. If the cast fails a
panic will be generated.**:?** checks if the cast is possible. Returns either
*True*, if it can be casted to the requested type, otherwise *False*.

*Down-casting* can be done at compile time, because the type to cast to is a
subset of the object type. *Up-casting* can only be done at runtime, because
the object type is a subset of the target type.
