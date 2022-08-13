---
chapter: 2
page: 30
kind: typo
reporter: Chris00
date: 2022-08-13
---
In `impl<P1..=Pn> ForeignTrait<T1..=Tn> for T0`, `Tn` should be `Tm`
since there isn't a requirement that the number of generic type
parameters matches the number of generic parameters of `ForeignTrait`.

Interestingly enough, the RFC [uses `Tn`][rfc], though I couldn't find
any rationale for why, and it is almost certainly just a typo. See also
[this discussion].

[rfc]: https://rust-lang.github.io/rfcs/2451-re-rebalancing-coherence.html#concrete-orphan-rules
[this discussion]: https://github.com/jonhoo/rust-for-rustaceans.com/pull/24
