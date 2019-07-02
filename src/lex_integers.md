### Integers

Integers are digit sequences, which depending on the prefix, allow different
characters. The digit sequences must be at least one digit long (prefix
excluded).

Decimal integers, which don't have a prefix, but cannot start with 0. They use
the decimal digits. Example:

```
0
100
44
// but not: 0
```

Hexidecimal integers (base 16) start with the prefix '0x'. They use decimal
digits and the letters A - F, both lowercase and uppercase. Example:

```
0xFF
0x10
0xFA1
// but not: 0x
```

Octal integers (base 8) start with the prefix '0o'. The use the digits 0 - 7.
Example:

```
0o1
0o71
// but not: 0o
```

To further denote the data type of the integer, suffixes are used. If no suffix
is used the data type is int32.

- u: Can be front of the suffixes s, S, l and L. Denotes that the data type
is unsigned.
- s: Very short. Data type is i8 or u8 if preceeded by u.
- S: Short. Data type is i16 or u16 if preceeded by u.
- l: long. Data type is i32 or u32 if preceeded by u.
- L: Very long. Data type is i64 or u64 if preceeded by u.

All other letters are invalid, resulting in an error. So

```
0z
0h
0j
```

are considered invalid. Also letters after the suffix are invalid. Therefore

```
0ula
0la
100sD
```

are all invalid.

