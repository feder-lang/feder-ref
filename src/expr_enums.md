## Enumerations

Enumerations have consist of several constructors. Each constructor can
be accompanied by a tuple with types. The tuple can be extracted with the match
expression. All constructors are added to the parent environment. An enumeration
has an own environment which is not added to the parent environment which stores
template variables. A reference to the enum type will be added to the parent
of environment. The reference is called like *id* in *enumdecl*.
