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


## Dive into `julia-parser.scm`

After the aperitif, let's move to our real target: understand [`julia-parser.scm`](https://github.com/JuliaLang/julia/blob/master/src/julia-parser.scm) and modify it.
The `do`-related function is,

```scheme
(define (parse-do s)
  (with-bindings
   ((expect-end-current-line (input-port-line (ts:port s))))
   (without-whitespace-newline
    (let ((doargs (if (memv (peek-token s) '(#\newline #\;))
                      '()
                      (parse-comma-separated s parse-range))))
      `(-> (tuple ,@doargs)
           ,(begin0 (parse-block s)
                    (expect-end s 'do)))))))
```

Some functions are used here:

### `with-bindings`
This function comes from the femtoLisp standard library.

```scheme
(define-macro (with-bindings binds . body)
(let ((vars (map car binds))
    (vals (map cadr binds))
    (olds (map (lambda (x) (gensym)) binds)))
    `(let ,(map list olds vars)
    ,@(map (lambda (v val) `(set! ,v ,val)) vars vals)
    (unwind-protect
    (begin ,@body)
    (begin ,@(map (lambda (v old) `(set! ,v ,old)) vars olds))))))
```

To understand it, we have to figure out what

* `define-macro`
* the `` ` `` notation in `` `(blabla) ``
* the `` , `` notation in `` ,(blabla) `` and `` ,v ``
* the `` ,@ `` notation in `` ,@(blabla) ``

are talking about.
From [documentation](http://www.gnu.org/software/mit-scheme/documentation/mit-scheme-ref/Lists.html#Lists)

<blockquote>the forms 'datum `datum ,datum, and ,@datum denote two-element lists whose first elements are the symbols quote, quasiquote, unquote, and unquote-splicing, respectively. The second element in each case is datum.</blockquote>

### `expect-end-current-line`
This is a little bit strange. A number?

```scheme
(define expect-end-current-line 0)
```

### `input-port-line`
It is a builtin function which recieves a port and returns the line number.
Note that `port` is the I/O stream for scheme.

### `ts:port`
Note: `aref` is the common-lisp name for `vector-ref`.
<i>i.e.</i>, get the $i$-th element of a vector.

```scheme
        (define-macro (ts:port s) `(aref ,s 1))
```
