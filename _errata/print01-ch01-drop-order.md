---
chapter: 1
page: 9
kind: inaccuracy
reporter: mbroso
date: 2026-01-04
---

It says, "In general, later variables may contain references to earlier values, whereas the inverse cannot happen due to Rust's lifetime rules. And for that reason, Rust drops variables in reverse order."
This is worded too strongly, its not the case that an earlier value cannot hold a reference to a later one (see below code snippet), but rather that if you do so, then the earlier value must be dropped first. Since this is a consequence of the reverse drop order, it might help to add another motivation for the reverse drop order (e.g. to be in line with non Drop types and and last in first out of stack variables).

```rust
struct A<'a>(Option<&'a B>);
impl<'a> Drop for A<'a> {
    fn drop(&mut self) {
        println!("drop A");
    }
}

struct B;
impl Drop for B {
    fn drop(&mut self) {
        println!("drop B");
    }
}

fn main() {
    let mut a = A(None);
    let b = B;
    a.0 = Some(&b);
    drop(a);
    drop(b);
    // Without manually invoking drop, Rust would fail with reverse order
    // drop(b);
    // drop(a);
}
```

