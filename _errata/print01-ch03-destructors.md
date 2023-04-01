---
chapter: 3
page: 47
kind: wording
reporter: lauti7
date: 2023-03-31
---
You says: 
"The second workaround is to make each of your fields takeable. You can "take" an Option by replacing it with None (which is what Option:: take does), but you can do this with many other types as well. For example, you can Take a vecOr HashMap by simply replacing them with their cheap-to-construct default values--std::mem::take is your friend here. This approach works great if your types have sane "empty" values but gets tedious if you must wrap nearly every field in an Option and then modify every access of those fields with a matching unwrap."

I think that in the last sentence "This approach..." you start referring to the `std::mem::take` because you talk about "empty" values, and what `std::mem::take` does is to replace the value with the `Default` implementation and then you end talking about `Option` saying "but gets tedious ...". I think the last sentence is not pretty clear this way. Maybe I'm misunderstanding something