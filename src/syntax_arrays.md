## Arrays

> expr := *indexcall* | *arraytypeexpr* | *array-constructor* | *arraylist*\
> *arraytypeexpr* := *expr* *arratype*\
> *arraytype* := **[** **]**\
> *arraytypes* := *arraytype* | *arraytype* *arraytypes*\
> *indexcall* := *expr* **[** *expr* **]**\
> *arraylist* := *expr0*? **[** *arraylist-tuple* **]**\
> *arraylist-tuple* := *expr1* | *expr1* **,** *arraylist-tuple*\
> *array-constructor* := *expr0*? **[** *expr2* **;** *expr3* **]**

Where: *expr0* is a type-check. The resulting array-type of the *arraylist* or
*array-constructor* created after '*expr0*?' must be the same as the type
*expr0*. *expr1* isn't a tuple. *expr2* is the base value for all array
elements. *expr3* is the size of the array and must evaluate to **uint64**.

*arraylist* has higher precedence than *indexcall*. So tuble-expressions won't
be an *indexcall* but an *arraylist*.
