---
chapter: 5
page: 70
kind: typo
reporter: Joel Posti
date: 2023-08-14
---

The last sentence of the second paragraph says

> Similarly, `if cfg!(feature = "some-feature")` is equivalent to `if true` only if the `derive` feature is enabled

but it should say

> Similarly, `if cfg!(feature = "some-feature")` is equivalent to `if true` only if the `some-feature` feature is enabled
