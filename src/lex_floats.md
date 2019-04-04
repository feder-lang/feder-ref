### Float-point numbers

Floating-number are two decimal digit sequences separated by '.'. Both
sequence must have at least one digit. Example:

```
0.0
0.123
123.5
```

To further denote the data type of the floating-point number, suffixes are used.
If no suffix is used the data type is float64.

- f: Single precision float. Data type is float32.
- F: Double precision float. Data type is float64.

All other letters are invalid, resulting in an error. So

```
0.0a
0.1d
```

are considered invalid.
