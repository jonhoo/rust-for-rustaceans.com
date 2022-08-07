---
chapter: 1
page: 15
kind: code
reporter: Ihor Taranenko
date: 2022-08-07
---

Listing 1-10 uses the signature

```rust
fn next(&self) -> Option<Self::Item>
```

for `Iterator::next`, but it should be

```rust
fn next(&mut self) -> Option<Self::Item>
```
