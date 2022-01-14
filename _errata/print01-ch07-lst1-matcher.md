---
chapter: 7
page: 103
kind: code
reporter: AJ ONeal
date: 2022-01-09
---

Listing 7-1 has three closing parens

```rust
macro_rules! test_battery {
  ($($t:ty as $name:ident),*)) => {
    // ...
  }
}
```

but should have only two

```rust
macro_rules! test_battery {
  ($($t:ty as $name:ident),*) => {
    // ...
  }
}
```
