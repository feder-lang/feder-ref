# Feder Reference Manual

Feder is an imperative programming language, which focuses on runtime speed,
intuitive design and more reliable programs. As such, Feder uses a garbage
collection, looks a lot like script-like programs and doesn't have
null-pointers.

## Download

Clone and jump into main directory:

```bash
git clone https://github.com/federlang/feder-ref
cd feder-ref
```

## Build

Install [mdbook](https://github.com/rust-lang-nursery/mdBook) using
[cargo](https://github.com/rust-lang/cargo) and build the book:

```bash
cargo install mdbook
mdbook build
```

This generates files in the directoy *docs*.
