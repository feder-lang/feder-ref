## Save

Safe allocation.

> *expr* := **safe** *arry-constructor* | **safe** *idcall* **(** *expr* **)**

Returns an [Option](./kernel_option.md). None is returned, if dynamic
allocation failed, otherwise Some.
