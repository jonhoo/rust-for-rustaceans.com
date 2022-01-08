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

The paragraph in question should be replaced with:

> Sometimes, you don't know if your code must own data or not, as it is
> runtime dependent. For this, the `Cow` type is your friend. It lets
> you represent data that _may_ be owned by holding either a reference
> or an owned value. If asked to produce an owned value when it only has
> a reference, a `Cow` uses the `ToOwned` trait to make one behind the
> scenes, usually by cloning. `Cow` is typically used in return types to
> represent functions that sometimes allocate. For example,
> `String::from_utf8_lossy` allocates only if the input contains invalid
> UTF-8. `Cow` can also be used in arguments for functions that can
> sometimes make use of owned inputs, but that's rarer in practice.
