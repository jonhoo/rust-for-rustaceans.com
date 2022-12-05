---
chapter: 3
page: 40
kind: advice
reporter: alex_xiong_
date: 2022-12-04
---

The "Wrapper Types" section suggests that `Deref` functions _a little
like_ inheritance, which may mislead readers to using it to emulate OO
in Rust, which is [a bad idea]. At the time of writing, the API
guidelines [recommend] only using `Deref` for smart pointer types (see
also [this SO answer]), though [this may change] to apply more broadly
to is-a newtypes, which is what the book should also recommend.

[a bad idea]: https://rust-unofficial.github.io/patterns/anti_patterns/deref.html
[recommend]: https://rust-lang.github.io/api-guidelines/predictability.html#only-smart-pointers-implement-deref-and-derefmut-c-deref
[this SO answer]: https://stackoverflow.com/questions/45086595/is-it-considered-a-bad-practice-to-implement-deref-for-newtypes
[this may change]: https://github.com/rust-lang/api-guidelines/issues/249
