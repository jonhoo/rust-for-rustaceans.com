---
chapter: 2
page: 22
kind: inaccuracy
reporter: forutan
date: 2024-02-06
---

In part which talk about layout represenation in C "[...] need to determine the alignment of Foo [...] use the largest alignment of any of Foo’s fields[...]"
Which seem wrong to me (or at least it wasn't clear).
The alignment of whole struct doesn't depend on largest alignment of fields, it just depends on underlying architecture.
Consider following code:

```rust
use std::mem;

#[repr(C)]
struct Bar {
    a: u64,
    b: u64,
    c: u64,
}

#[repr(C)]
struct FOO {
    bar: Bar,
    a: u64,
    b: u64
}

fn main() {
    println!("{}", mem::size_of::<Bar>()); // 24
    println!("{}", mem::size_of::<FOO>()); // 40
}
```

Obviously 40 is not a multiple of 24!
