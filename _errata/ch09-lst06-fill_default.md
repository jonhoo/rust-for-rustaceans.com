---
chapter: 9
page: 158
kind: code
reporter: monoid
date: 2021-12-22
# fixed: 2021-01-01
---
Listing 9-6 says

```rust
self.set_len(start + n);
```

but should say

```rust
self.set_len(start + fill);
```
