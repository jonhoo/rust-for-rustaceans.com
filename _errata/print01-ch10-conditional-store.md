---
chapter: 10
page: 187
kind: inaccuracy
reporter: nicarran
date: 2024-01-31
---

In paragraph 2 of the COMPARE_EXCHANGE_WEAK box, the text reads:

> For example, ARM processors instead have locked load and conditional
> store operations, where a conditional store will fail if the value
> read by an associated locked load has not been written to since the
> load.

The "not" there is erroneous, and the sentence is unclear. The sentence
should read:

> For example, ARM processors instead have locked load and conditional
> store operations, where a conditional store will fail if the value
> read by an associated locked load has been written to at all, _even
> with the same value_, since the load.
