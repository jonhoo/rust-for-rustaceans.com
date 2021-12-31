---
chapter: 11
page: 202
kind: typo
reporter: monoid
date: 2021-12-27
# fixed: 2021-01-01
---
The sample gives `Option<*mut T>` as niche optimization used across FFI boundaries.  However, the `*mut T` is nullable, and is not subject to the niche optimization.  So, `Option<NotNull<T>>` should be used as an example.
