# Introduction

Feder is an imperative programming language, which focuses on runtime speed,
simple, yet powerful design and more reliable programs. As such, Feder features

- Garbage collection: Don't care about memory-management
- No null pointers: Prevent typical errors from languages like C, C++, Java
- Tuples & tuple-based enumerations: Functions can return several objects,
  no need for a custom class or state-bound objects
- Templates
- Parts from functional programming
- Parts from object-oriented languages
- Ensurance (Contracts): Compile-time runtime-exceptions

## Target audience

Targeted are those, who seek in-depth knowledge about Feder. This is by no
means a guide for beginners.

## Example program

A hello world program

```
import std

func main
	null io.out.println("Hello, World!")
;
```

which prints

```
Hello, World!
```

to standard output.
