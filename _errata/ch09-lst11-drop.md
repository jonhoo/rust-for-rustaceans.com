---
chapter: 9
page: 162
kind: code
reporter: Nick Massey
date: 2021-10-07
# fixed: 2021-01-01
---
Listing 9-11 says

```rust
unsafe impl<#[may_dangle] T> for Box<T> { /* ... */ }
```

but should say

```rust
unsafe impl<#[may_dangle] T> Drop for Box<T> { /* ... */ }
```
