---
chapter: 9
page: 152
kind: code
reporter: necabo
date: 2022-02-20
---

Listing 9-4 declares pub trait methods as public

```rust
pub unsafe trait GlobalAlloc {
    pub unsafe fn alloc(&self, layout: Layout) -> *mut u8;
    pub unsafe fn dealloc(&self, ptr: *mut u8, layout: Layout);
}
```

but pub is not permitted on pub trait methods because it's implied

```rust
pub unsafe trait GlobalAlloc {
    unsafe fn alloc(&self, layout: Layout) -> *mut u8;
    unsafe fn dealloc(&self, ptr: *mut u8, layout: Layout);
}
```
