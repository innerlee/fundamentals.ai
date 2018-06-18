---
layout: post
title:  "A tour to Lisp"
date:   2018-06-18
excerpt: "The Scheme dialect."
image: "/images/sicp.jpg"
---

At first, it seems that the only difference between lisp and other programing languages is the writing style:
in Julia, it is

```julia
+(1, 2)
```

and in Scheme, a dialect of of Lisp,

```scheme
(+ 1 2)
```

Other than the placement of brackets, there do not seem much difference.
...Until, an exercise in [sicp](https://mitpress.mit.edu/sites/default/files/sicp/index.html) came up:

```scheme
(define (a-plus-abs-b a b)
    ((if (> b 0) + -) a b))
```

Here, the operator `+` or `-` is determined by some condition.
This clearly shows the benefit of the arrangement of brackets in Lisp:
easily manipulate functions just as any data.
