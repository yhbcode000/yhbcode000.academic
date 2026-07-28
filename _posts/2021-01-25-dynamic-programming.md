---
layout: single
title: "Tabulation v.s. Recursion with Memory (Dynamic programming)"
date: 2021-01-25 14:05:22
author_profile: true
---

## Question

DP vs Recursion with memorization

I am wondering if that for any recursive function that can be translated into dynamic programming, is it always possible to also simply leave the function in its recursive form and apply a memorise wrapper to it as well? While we have clearly been shown there are many benefits to turning something into dynamic programming, I feel like some functions may be a lot easier to understand if they are in a recursive form and using a memorise function should help keep running costs low.

Such as the example in lecture 17 with seam carving, in my mind it would be considerably easier to understand what a function was doing if it worked backwards from the end point and recursively found the best path to that point, all why keeping running costs low due to a memorise wrapper.

## My Answer

In my opinion, the bottom-up method and the top-down with memory (or recursive with memory) are **quite similar methods**  (or they wouldn't be classified as dynamic programming together).

1. They both keep something in a list (maybe dimension higher than 1)
2. They both cut off the calculated recursion tree. Make sure recursion runs under polynomial-time.

The difference between them is the way they fulfill the memory space and how they cut the recursion tree.

| top-down with memory                                               | bottom-up                                                                                |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------- |
| generate data in memory in a passive way                           | generate data in memory in an active way                                                 |
| when recursion algorithms visit a node, we store information       | when we visit nodes in whatever order we like and then store information                 |
| when visiting a stored node, we call its value from memory         | after observing the pattern of whole memory, we go through all nodes without repeatation |
| we compute while storing information while cutting redundant trees | we fulfill memory, then we find a way to cut redundant trees, and finally, we compute    |

Hope this comparison table can help you with understanding.

(By the way, I think memory decorator is easier to understand and much more to implement too.)
