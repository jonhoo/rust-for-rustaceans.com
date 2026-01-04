---
chapter: 1
page: 9
kind: inaccuracy
reporter: mbroso
date: 2026-01-04
---

I'm a bit confused by the explanation for the inverse drop order when variables go out of scope.
It says, "In general, later variables may contain references to earlier values, whereas the inverse cannot happen due to Rust's lifetime rules. And for that reason, Rust drops variables in reverse order."
Maybe I'm getting it wrong, but in my opinion the inverse case that an earlier variable may contain references to later values can happen and is not forbidden by Rust's lifetime rules (even though the other case is much more common). In the following code snippet the earlier variable `b` contains a reference to the later variable `a2` and its fine if `b` is dropped before `a2`. Thus, in this example the inverse drop order is not appropriate.

```rust
struct A(u32);
impl Drop for A {
    fn drop(&mut self) {
        println!("drop A {}", self.0);
    }
}

struct B<'a>(&'a A);
impl<'a> Drop for B<'a> {
    fn drop(&mut self) {
        println!("drop B");
    }
}

fn main() {
    let a1 = A(1);
    let mut b = B(&a1);
    let a2 = A(2);
    b.0 = &a2;
    drop(b);
    drop(a2);
    drop(a1)
    // Without manually invoking drop, Rust would fail with the inverse order
    // drop(a2);
    // drop(b);
    // drop(a1);
}
```

Am I missing something here, or would it help to slightly rephrase the explanation of the inverse drop order?

