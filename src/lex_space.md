### Space

Space characters are the space character, the tab character, the vertical tab
character and form-feed character and region-comments. Space characters are
ignore, therefore is optional, except when used to seperate tokens.

These means, the following expressions

```
1 + 2
```

and

```
1+2
```

do the very same at runtime.

Spaces are not ignore in strings or character constants. Therefore

```
"my      token"
```

isn't the same as

```
"my token"
```

Also newlines following a newline are regarded as space. This means the
expressions

```
trait MyTrait
	Func myfunc ;
;
```

and

```
trait MyTrait

	Func myfunc ;
;
```

represent equal semantics.
