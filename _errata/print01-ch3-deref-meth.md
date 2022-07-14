---
chapter: 3
page: 41
kind: wording
reporter: @Chris00
date: 2022-07-14
---
In the box “Deref and inherent methods”, the intent would have been
clearer from the first sentence if it read “`Deref` can get confusing
and surprising when there are methods on `T` that take `&self`”
(instead of `self`).  Indeed, as `deref` returns a reference, there is
no ambiguity if the method indeed takes `self`.

BTW, I was a bit surprised that `DerefMut` (or `AsMut`) was not even
mentioned.
