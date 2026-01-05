---
chapter: 1
page: 9
kind: inaccuracy
reporter: mbroso
date: 2026-01-04
---

I'm a bit confused by the explanation for the reverse drop order when variables go out of scope.
It says, "In general, later variables may contain references to earlier values, whereas the inverse cannot happen due to Rust's lifetime rules. And for that reason, Rust drops variables in reverse order."
Maybe I'm getting it wrong, but the inverse case that an earlier variable may contain references to later values can happen and is not forbidden by Rust's lifetime rules (even though the other case is more common). In the following code snippet the earlier variable `a` contains a reference to the later variable `b` and its fine if `a` is dropped before `b`. Thus, in my example the reverse drop order is not appropriate.

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

Am I missing something here, or would it help to slightly rephrase the explanation of the inverse drop order? (e.g. to be in line with non Drop types and last in first out of stack variables)

