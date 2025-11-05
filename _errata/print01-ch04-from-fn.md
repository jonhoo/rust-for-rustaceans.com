---
chapter: 4
page: 63
kind: code
reporter: joserlopes
date: 2025-11-05
---

The function defined as: `fn<T>(T) where Foo: From<T>` should be: `fn<T>(Foo: T) where Foo: From<T>`.
