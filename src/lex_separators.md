### Separators

Characters, which separate tokens are the line-feed and
carriage-return character and also:

```
( ) [ ] { } ;
```

*Later on, the line-feed character and carriage-return character are simply
refered to as newline characters.*

Also line-comments are treated the same as newline characters. They are started
with // and range till the next newline character. Therefore

```
myFunction()
```

is the same as

```
myFunction() // this is a function call
```

[Operators](./lex_operators.md) are also separators.
