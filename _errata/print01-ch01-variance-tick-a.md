---
chapter: 1
page: 16
kind: clarification
reporter: Chris00
date: 2022-08-13
---
This page should have a note between the second and third paragraph that
reads

> The `'a` in the example types listed here do not refer to a generic
> lifetime gathered from `<'a>`. Instead, it refers to some _concrete_
> lifetime that is not `'static`, such as that assigned to the type of
> `x` in a statement such as `let x = &some_variable`.
