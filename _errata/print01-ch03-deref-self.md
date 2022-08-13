---
chapter: 3
page: 41
kind: wording
reporter: Chris00
date: 2022-08-13
---
The box "Deref and Inherent Methods" should say

> methods on `T` that take `&self`

That is, it should say `&self` rather than `self` to match the actual
definition of the `Deref` trait.

The box should also mention `DerefMut` and `AsRef`, both of which have
the same auto-dereference behavior.
