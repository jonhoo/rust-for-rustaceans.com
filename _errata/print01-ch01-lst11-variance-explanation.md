---
chapter: 1
page: 17
kind: inaccuracy
reporter: Yoav Orot
date: 2025-02-17
---

In the first paragraph after the `NOTE` section, where the text describes
listing 1-11, it says:

> At 1, the compiler must determine what lifetime the lifetime parameter(s)
> should be set to. If there are two lifetimes, `'a` is set to the to-be-
> determined lifetime of the borrow of `s`, and `'b` is set to `'static` since
> that’s the lifetime of the provided string `"hello"`. If there is just one
> lifetime `'a`, the compiler infers that that lifetime must be `'static`.

It should be noted that lifetime `'b` (or `'a` in the single lifetime scenario)
is not set to `'static`, but to a coerced supertype of `'static` that is
computed for the reference held by the `s` variable.

Then, in the third paragraph after the `NOTE` section:

> While `&'static str` can in general be shortened to any `&'a str` (`&'a T` is
> covariant in `'a`), here it’s behind a `&mut T`, which is invariant in `T`.

We should, as above, note that lifetime `'a` is not set to be `'static`, but to
the supertype that was computed for the reference in `s`.

If, in the single lifetime scenario, lifetime `'a` were actually set to
`'static` (e.g. by writing `let mut s: &'static _ = "hello";`), listing 11 would
not compile, even without the `println!("{}", s);` line, as the compiler would
have complained that the `s` variable is dropped at the end of the function
while still being borrowed.

However, in this case, as part of Rust's lifetime subtyping, the lifetime of the
borrowed `str` reference in the `s` variable is shortened only until the last
usage of `s`, which is `println!("{}", s);`. This sets the lifetime of `'a` to
include the aforementioned `println` line, which in turn leads to the mutable
borrowing of the `s` variable (in `s: &mut s`) using the same lifetime duration.

In other words, if `MutStr` had only one lifetime, instead of two, the `s`
variable would have been mutably borrowed until the end of its own variable's
lifetime.
