## Environment

An environment is assembly of semantics[^sem] which can be referenced by an
*identifier*[^id]. There can be semantics with the same *identifier*, when this is
the case, a reference will point to the newest semantic. The environment has
either no parent (if it is the environemnt of the whole document) or one
parent.

[^sem]: All function bodies, program-bodies, modules and classes(only
        functions) have an own environment.

[^id]: This is also *funcvars* or *template* not just the *id*.

### Shadowing

As mentioned above, semantics with the same *identifier* can be added
to a single *environment*. This is only possible, if:

- The previous semantic in the environemnt is a variable
- The semantic is an template specialization of of the previous semantic
  (where all semantics which are already specializations are ignored).
