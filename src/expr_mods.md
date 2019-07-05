## Modules

Modules separate code by functionality. A module has an own environment and
is added as *id* from *moduledecl* to the parent environment. A module's
*id* must start with an lowercase, alphabetic character.

Libraries are also just modules.

### Variables

Variables in modules can be either **global**, if the module has only modules
and library as parents otherwise the variable is **local**.
