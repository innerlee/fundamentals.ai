---
layout: post
title:  "Splatting in Julia"
date:   2018-05-23
excerpt: "Splatting is handy, splatting is slow."
image: "/images/julialang.svg"
---

<a href="https://julialang.org/">Julia</a> is on the verge of being <a href="https://discourse.julialang.org/t/1-0-progress-status/9762">1.0</a>.
I have been using Julia for three years, and felt that it is really nice and elegent a language.
The syntax is predictable and gramma intuitive.
There are two kinds of Julia users in general.
One kind of user pursues speed.
They would care every detail that would affect code performance.
The other kind of user, like me, weight elegance more than sheer performance.
Splatting is beautiful in its appearance, but people of the first kind often jump out and warns you: use splatting with care! do not use them for large lists! etc., etc...

So, what splatting is?
