## Templates

Every behaviour of an object, which have the template type as type, must be
provided by the template variable. This is realized with traits, which declare
the behaviour.

Semantics which declare templates, must have defined behaviour. They cannot
have declared behaviour.

It is possible to use the template type in its own template definition. Template types cannot
be access by previous template types.

If *id1* is used, then *id0* can be omitted, when resolving the template. *id1*
must be a valid template type used in previously in the same template
declaration.

```
class{T: std.StdField} MyVectorClass0
  T x;
  T y;

  func MyVectorClass0(x: T, y: T)
	this.x = x;
	this.y = y;
  ;
;

class{T, D=T} MyTemplateClass0
;

func main
  var0 := MyTemplateClass0{std.u8}();
  var1 := MyTemplateClass0{std.u8, std.u16}();
  var2 := MyTemplate
;
```
