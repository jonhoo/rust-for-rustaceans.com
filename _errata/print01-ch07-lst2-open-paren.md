---
chapter: 7
page: 103
kind: code
reporter: nmarley
date: 2023-01-05
---

Listing 7-2 calls the `test_battery` macro with an open brace `{`:

```rust
...
test_battery! {
  u8 as u8_tests,
  // ...
  i128 as i128_tests
);
```

... instead of an open paren `(`:

```rust
...
test_battery! (
  u8 as u8_tests,
  // ...
  i128 as i128_tests
);
```
