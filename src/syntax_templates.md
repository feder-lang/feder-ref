## Templates

> *templ-decl* := **{** *templ-decl-params* **}**\
> *templ-decl-params* := *templ-decl-param* | *templ-decl-param* **,** *templ-decl-params*\
> *templ-decl-param* := *vardecl* | *id*\
> *templ-call* := **{** *templ-call-params* **}**\
> *templ-call-params* := *templ-call-param* | *templ-call-param* **,** *templ-call-params*\
> *templ-call-param* := *idcall*

where *id* or LHS of *vardecl* are the template-type names. RHS of *vardecl*
are trait(s) the template-type has. Only functions defined by these traits can
be used as members of the template-type(-values).

*idcall* is the type to replace the template-type with.
