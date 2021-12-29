---
chapter: 13
page: 235
kind: code
reporter: monoid
date: 2021-12-27
# fixed: 2021-01-01
---
Listing 13-3 says

```rust
impl Drop for DropGuard<'_> {
    fn drop(&mut self) {
        lock.store(true, Ordering::Release);
    }
}
```

but should say

```rust
impl Drop for DropGuard<'_> {
    fn drop(&mut self) {
        self.0.store(true, Ordering::Release);
    }
}
```
