---
chapter: 8
kind: code
reporter: jonhoo
page: 121
date: 2023-12-17
# fixed: 2021-01-01
---
The various listings and text in the sub-section "Ergonomic Futures" in
chapter 8 uses `Receiver::next` and `Receiver::receive` interchangeably.
This is confusing, since it means the text occasionally does not agree
with the listed code (e.g., the last paragraph on page 125 refers to
`Receiver::next` in Listing 8-4, which has no such call).

There is no good reason for some of the listings to use one and others
to use the other.

The text and code should be updated such that every call to `.receive`
and mention of `Receiver::receive` should be changed to `.next` and
`Receiver::next` respectively. It should use `next` consistently as that
is the generally agreed-upon convention for getting the next value from
a stream (which `Receiver` represents).
