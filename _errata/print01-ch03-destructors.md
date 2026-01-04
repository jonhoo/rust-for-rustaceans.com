---
chapter: 3
page: 47
kind: wording
reporter: lauti7
date: 2023-03-31
---
The paragraph that reads, in part:
> The second workaround is to make each of your fields takeable. You can "take" an Option by replacing it with None (which is what `Option::take` does), but you can do this with many other types as well. For example, you can take a Vec or HashMap by simply replacing them with their cheap-to-construct default values — `std::mem::take` is your friend here. This approach works great if your types have sane "empty" values but gets tedious if you must wrap nearly every field in an Option and then modify every access of those fields with a matching unwrap.

This paragraph is technically correct, but somewhat hard to follow, because "empty" and default are not necessarily the same thing. Some types implement `Default`, but that value is not technically "empty" (`usize` for example). The sentence should instead read:

>  [..] have sane default values (like an empty map or a `None`) but gets tedious if you must wrap nearly every field in something like an `Option` [..]