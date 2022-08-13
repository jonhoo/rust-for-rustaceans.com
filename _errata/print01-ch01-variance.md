---
chapter: 1
page: 16
kind: inaccuracy
reporter: Chris00
date: 2022-08-13
---
The sentence that starts "All types have a variance" should instead
read:

> All types with generic parameters (be they lifetime or type
> parameters) have a variance with respect to those parameters. That
> variance defines what …

Types with no generic parameters do not "have a variance". Variance is
always defined in relation to a parameter.
