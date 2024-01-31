---
chapter: 10
page: 187
kind: inaccuracy
reporter: nicarran
date: 2024-01-31
---

On COMPARE_EXCHANGE_WEAK paragraph 2, it is said:
"
For example, ARM processors instead have 
locked load and conditional store operations, where a conditional store will fail 
> if the value read by an associated locked load has not been written to since 
the load. 
"

It should say (remove "not" on line marked by >):
"
For example, ARM processors instead have 
locked load and conditional store operations, where a conditional store will fail
> if the value read by an associated locked load has been written to since 
the load.
"
