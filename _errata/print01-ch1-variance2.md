---
chapter: 1
page: 16
kind: inaccuracy
reporter: @Chris00
date: 2022-07-14
---
The part “if a function takes a `&mut Vec<&'a str>`, you cannot pass it
a `&mut Vec<&'static str>`” is confusing as `'a` is likely to be read
as a type variable while you mean “[a concrete lifetime a][]”.  IMHO
this part should be expanded and an example should be added.


[a concrete lifetime a]: https://twitter.com/jonhoo/status/1546971235409571843
