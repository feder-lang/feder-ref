### Characters

A character constant is enclosed within single quotation marks, such as 'a'.
Between the quotation marks is usually a single printable character, except
character which cannot be represented, like the single quotation mark itself.
They are represented with escape sequences, which start with \\.

```
\'
  Single quotation mark

\"
  Double quotation mark

\\
  Backslash

\a
  Bell

\b
  Backspace

\f
  Formfeed page break

\n
  Newline (line feed)

\r
  Carriage return

\t
  Horizontal tabulator

\v
  Vertical tabulator

\xXX
  Byte represented with two XX hexadecimal characters
```

All other character following \\ are invalid.
