---
chapter: 11
page: 207
kind: inaccuracy
date: 2022-02-01
---
The sentence

> Since `Foo` and `Bar` are zero-sized types, they can be used in place of `()`
> in the `extern` method signatures.

in the final paragraph of the  "Pointer Confusion" section is inaccurate. Both
`Foo` and `Bar` are `#[repr(transparent)]` wrappers over a `c_void`, but
`c_void` is not equivalent to `()`, and its size is in fact 1 rather than 0.

For a deeper explanation of why `c_void` must not be zero-sized, see
https://github.com/rust-lang/rust/blob/1be5c8f90912c446ecbdc405cbc4a89f9acd20fd/library/core/src/ffi.rs#L26-L33

The sentence in question should be replaced with:

> Since `Foo` and `Bar` are identical to `c_void` in size and alignment, they
> can be used in place of the latter in the `extern` method signatures.