---
chapter: 7
page: 103
kind: code
reporter: nmarley
date: 2023-01-05
---

Listing 7-2 closes the `test_battery` macro invocation with a closing paren and semicolon `);`:

```rust
...
test_battery! {
  u8 as u8_tests,
  // ...
  i128 as i128_tests
);
```

... instead of a closing brace `}`:

```rust
...
test_battery! {
  u8 as u8_tests,
  // ...
  i128 as i128_tests
};
```
