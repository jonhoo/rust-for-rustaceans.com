---
chapter: 1
page: 24
kind: code
reporter: iwahbe
date: 2021-12-24
---
The code formatting on iBooks is always wrong. I see correct highlighting  distinction
between comment and code, but neither indentation or lines are correct. 

This is the listing 1-7 as I see it (indentation and line breaks) on iBooks:
```rust
fn replace_with_84(s: &mut Box<i32>) { // this is not okay, as *s would be empty: {1}
// let was = *s; // but this is:{2} let was = std::mem::take(s); // so is this: {3} *s =
was; // we can exchange values behind &mut: let mut r = Box::new(84);{4}
```

I am replacing the numbered tags with `{n}`. 
