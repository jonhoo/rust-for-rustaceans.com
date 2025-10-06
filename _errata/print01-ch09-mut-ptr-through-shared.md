---
chapter: 9
page: 156
kind: inaccuracy
reporter: ijchen
date: 2025-10-06
# fixed: 2021-01-01
---
The following is inaccurate:

> ...so if you have an `&` to a type that contains a `*mut T`, you are not allowed to ever mutate
> the `T` through that `*mut` even though you could write code to do so using `unsafe`.

While it's true that you cannot mutate data *within* the `T` of a `&T` (including transitively),
this immutability does not travel through pointers. You cannot mutate the pointer itself (i.e., it
would not be okay to mutate the pointer's address), but this immutability does not prevent mutating
*through* pointers stored behind the reference.
