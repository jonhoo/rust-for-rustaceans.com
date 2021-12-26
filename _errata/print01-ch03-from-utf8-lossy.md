---
chapter: 3
page: 45
kind: inaccuracy
reporter: david-perez
date: 2021-12-26
# fixed: 2021-01-01
---
The sentence "For example, `String::from_utf8_lossy` needs to take ownership of
the byte sequence that is passed to it only if it contains invalid UTF-8
sequences." in the fourth paragraph of the "Borrowed vs. Owned" section is
inaccurate.
[`String::from_utf8_lossy`](https://doc.rust-lang.org/stable/std/string/struct.String.html#method.from_utf8_lossy)
_never_ takes ownership of the input byte sequence. What it does is it
leverages `Cow<'a, str>` to either return the same input bytes reinterpreted as
a string slice if they are valid UTF-8, or clone only the valid UTF-8 sequences
into a newly-allocated `String` otherwise.
