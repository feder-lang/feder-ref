### Guards

> *guard* := **|** *expr0* *guardresult*?\
> *guardresult* := **=>** *expr1*

Where: *expr0* is the guard condition and *expr1* the guard result.

Guards guard the function body from certain (invalid) arguments. The guard must
evaluate to the type [bool](./kernel_bool.md). The guard result will be
returned, if the guard evaluates to **False**.  If no guard result is given,
the guard will spawn a panic, if the guard evaluates to **False**. The guard
has to evaluate to the same type as the return-type of the function.

Guards must be implemented directly into the function. Meaning, that if the
function is called, its guards are not checked above the function call, but the
function itself will check the guards.
