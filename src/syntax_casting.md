## Casting

> expr := expr **::** expr\
> | expr **:?** expr

With **::** an complex-object is casted to another type. If the cast fails a
panic will be generated.**:?** checks if the cast is possible a return either
*True*, if it is, otherwise *False*.

*down-casting* can be done at compile time, because the type to cast to is a
subset of the object type. *up-casting* can only be done at runtime, because
the object type is a subset of the target type.
