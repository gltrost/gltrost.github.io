---
layout: post
title:  "A Guide To Subfields in Formal Methods"
date:   2021-01-24
excerpt: "An attempt at formalizing formal methods"
image: "/images/logic-book1.jpg"
type: "logic"
---

# What are all the major areas of Formal Methods, and how do they relate?

When I started majoring logic back in college, I was introduced to different
topics of logic one-by-one as they came to me in different classes. That said,
I regret there never being a moment when the heads of the department pulled
me aside and explained to me the landscape of what I was studying. Here's my
attempt.

# What I assume you already know:

1. A little bit of mathematical logic
2. A little bit of functional programming and/or how types work

# Versions of Semantics

## Operational Semantics: Algorithms defined as output
Operational semantics treats semantics of a program as the result of just
"running" the program, like you would run any program. So if you have some
OCaml code `let f (x : int) : int = x * 2`, then the "semantics" of, say,
`f(7)` is just `14`.
Something like `let g (x : int) : int = g(x + 1)` would have undefined semantics
for all values, since no input would halt. Another way of putting it is
"The meaning of a term t can be taken to be the final state
that the machine reaches when started with t as its initial state" (Pierce 32).
So the final state of running `f(7)` is `14`, where as `g(234)` is undefined:

## Denotational Semantics: Algorithms defined as some Mathematical function
Suppose you have some function
```
let exp1(int x, int y) : int =
  let result = ref 1 in
  while (!y > 1) do
    let result = !result * x
    decr y
  done;
  result
```
and another function
```
let rec exp2(int x, int y) : int =
  if (y == 1) then x else x * exp2(x,y-1)
```
and another function
```
let exp3(int x, int y) : int =
  case y of
  | 0 -> 1
  | 1 -> x
  | 2 -> x * x
  | 3 -> x * x * x
  ...
  | 4294967295 -> x * x * x * ... * x  
```
These all have the semantic meaning for 64-bit signed integers in OCaml.
Namely, they all represent the mathematical idea of exponentiation (with respect
to 64-bit signed ints, at least).

So in that sense, the semantic meaning of these functions is the underlying
function exp(x,y) = x^y.

## Axiomatic semantics

# Different Theories

## Hoare Logic

## Model Checking

## Type Theory

## Dynamic Logic
