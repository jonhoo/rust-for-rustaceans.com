---
chapter: 9
page: 142
kind: code
reporter: Callum Iddon
date: 2022-01-07
# fixed: 2021-01-01
---
Listing 9-1 says

```rust
impl<T> SomeType<T> {
    pub unsafe fn decr(&self) {
        self.some_usize -= 1;
    }
}
```

but should say

```rust
impl<T> SomeType<T> {
    pub unsafe fn decr(&mut self) {
        self.some_usize -= 1;
    }
}
```