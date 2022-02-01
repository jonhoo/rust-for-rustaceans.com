---
chapter: 11
page: 207
kind: inaccuracy
date: 2022-02-01
---
The sentence "Since `Foo` and `Bar` are zero-sized types, they can be used in
place of `()` in the `extern` method signatures." in the final paragraph of the
"Pointer Confusion" section is inaccurate. Both `Foo` and `Bar` are
`#[repr(transparent)]` wrappers over a `c_void`, but `c_void` is not equivalent
to `()`, and its size is in fact 1 rather than 0.

This confusion probably arose because the C `void` type is zero-sized. See
https://github.com/rust-lang/rust/blob/master/library/core/src/ffi.rs#L26-L33
for why Rust's `c_void` is not.

The sentence in question should be replaced with:

> Since `Foo` and `Bar` are identical to `c_void` in size and alignment, they
> can be used in place of the latter in the `extern` method signatures.