## Traits

They are added to the current
environment using the *id* in *traitdecl*. Traits have an own environment which
can't be referenced, which contains the template variables.

The environment of an object which has the trait as type, contains all declared
functions in *traitbody*. When referencing the fucntion a function without the
**this** or **This** parameter is returned.

The name of the trait (first expression *id* in *traitdecl*) must start with
an uppercase character with optional leading '_'.

### Trait inheritance

Traits can inherited function declarations from other traits with
*templidcalls*, where every *templidcall* must be a trait. Traits can't be
inherited if a the traits have functions with the same name and parameters.
