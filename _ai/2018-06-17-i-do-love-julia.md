---
layout: post
title:  "I do love Julia"
date:   2018-06-17
excerpt: "Fluent interface in Julia."
image: "/images/julialang.svg"
---

### What is fluent interface?

[Fluent interface](https://en.wikipedia.org/wiki/Fluent_interface) is a style on method chaining that possesses good readability
It is extensively used in languages such as C#.
One example is in data processing:

```csharp
var query = db
    .Where(i => i.Name.Contains("zz"))
    .OrderBy(i => i.Name.Length)
    .Select(i => i.Name.ToUpper());
```

Another example is in configuration:

```csharp
var host = new WebHostBuilder()
    .UseKestrel()
    .UseUrls("http://*:5000")
    .UseContentRoot(Directory.GetCurrentDirectory())
    .UseIISIntegration()
    .UseStartup<Startup>()
    .Build();
```

These two examples demonstrates that fluent interface is handy in some areas.

### How about fluent interface in Julia?

Unfortunately, Julia does not support fluent design well.
Partly, this is because Julia is not OO by design.
There are some features that approximately does something similar.
One is the pipe operator `|>` that allows for easy function chaining.
For example:

```julia
[1:5;] |> x->x.^2 |> sum |> inv
```

There are nothing to blame in its functionality
However, the operator `|>` itself is very ugly, and not friendly to typing
Besides, except for the first one, each part requires a function,
which requires lots of typing (the lambda protocol) if the function is not pre-defined.
For the first blame, it is a personal taste thing.
While for the second one, the trouble is genuine.
There is a pending [pull request](https://github.com/JuliaLang/julia/pull/24990) that aim to make creating anonymous functions easier.
It treats underscore `_` as a special signal.
`f(_, y)` turns into `x -> f(x, y)`, and `_[i]` turns into `x -> x[i]`.
This greatly reduces the characters we need to type for creating a function.
So the second problem is solved to some extent.
Let's turn to the first one.

### `do`

The `do` syntax is a special one in Julia. Let's look at an example.

```julia
map(1:10) do x
    x^2
end
```

This is equivalent to `map(x -> x^2, 1:10)`.
When you use `do`, it assumes that the first argument of the previous function accepts a function.
And the definition of that function is defined right after the keyword `do`.

How about we use another word, say `dot`, and when `dot` appears,
it assumes the function after it takes an object as the first argument,
and feed the output of previous functions to it?
And if it is okay, how about not calling it `dot`, but reuse the term `do`?
For example,

```julia
love(a, b) = print("$a love $b")

"I" do love("Julia")
```

The last line would translate into `love(I, "everyone")`.
With this, the fluent interface is easy to implement.
And here is an example,

```julia
[1:5;] do (x->x.^2)() do sum() do inv()
```
### `broadcast`

This do not play nicely with <i>half</i> of the functions.
Because their first argument accepts a function.
One example is `map`.
`map` is used to do some element-wise transformation.
With the new `do` syntax, element-wise transformation is not easy to accomplish.
`broadcast` is our life saver.
consider this example:

```julia
[1:5;] .do (x->x^2)() do sum() do inv()
```

## Implementation

### Try 1: Macro

First I try to implement the idea using macros.
However, the first trouble is, the proposed `do` syntax is invalid.
They cannot pass the Julia parser, so the codes are blocked by errors before they arrived to macros.
Okay, how about use another word, say `dot`?

```julia
function rearrange(expr)
    if length(expr) > 2 && expr[2] == :dot
        insert!(expr[3].args, 2, expr[1])
        return rearrange(expr[3:end])
    else
        return expr
    end
end

macro dot(something...)
    esc(rearrange(something)[1])
end
```

Then the following code works as expected.

```julia
love(a, b) = print("$a love $b")

@dot "I" dot love("Julia")

@dot [1:5;] dot (x->x.^2)() dot sum() dot inv()
```

This is not satisfying because of the use of `dot`, and because the use of `@dot`.
To get rid of these annoyances, we need hack the Julia parser.

### Try 2: Parser

Let's do something to the parser.
