---
chapter: 2
page: 30
kind: typo
reporter: @Chris00
date: 2022-07-14
---
In `impl<P1..=Pn> ForeignTrait<T1..=Tn> for T0`, the two `n` should be
different (`impl<P₁,...,Pₙ> ForeignTrait<T₁,...,Tₘ> for T₀`).


P.S. I used on purpose real indices and `,...,` in order not to mix
the language and meta-language.
