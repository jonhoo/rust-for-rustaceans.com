---
chapter: 1
page: 9
kind: inaccuracy
reporter: mbroso
date: 2026-01-04
---

The book states

> In general, later variables may contain references to earlier values,
> whereas the inverse cannot happen due to Rust's lifetime rules. And
> for that reason, Rust drops variables in reverse order.

This is worded too strongly, as earlier values *can* hold a reference to
later ones, but then the earlier value must be (manually) dropped first.
The text should read:

> In general, later variables may contain references to earlier values
> (as they live longer), whereas the inverse is generally not permitted
> due to Rust's lifetime rules. And for that reason, Rust drops
> variables in reverse order. If an earlier variable is made to
> reference a later value, the earlier variable must be explicitly
> dropped first with `drop` or the code will not compile.
