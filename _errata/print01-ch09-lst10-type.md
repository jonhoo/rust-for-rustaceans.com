---
chapter: 9
page: 161
kind: code
reporter: Callum Iddon
date: 2022-01-11
# fixed: 2021-01-01
---
Listing 9-10 says

```rust
fn barify<’a>(_: &’a mut i32) -> Bar<Foo<’a>> { .. }
let mut x = true;
let foo = barify(&mut x);
x = false;
```

but should say

```rust
fn barify<'a>(_: &'a mut bool) -> Bar<Foo<'a>> { .. }
let mut x = true;
let foo = barify(&mut x);
x = false;
```