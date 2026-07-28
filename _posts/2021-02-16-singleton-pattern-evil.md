---
layout: single
title: "Why singleton design pattern is evil"
date: 2021-02-16 19:22:27
author_profile: true
---

## Key discussion

Is the singleton design pattern an antipattern?

> The singleton pattern is controversial. Some people go so far as to say singletons are evil. Others have likened singletons to sharks; they cruise along unnoticed under the surface, then pop up and bite you. We’re going to argue that it is an antipattern to be avoided at all costs. There are only a few legitimate uses for it –– we’ll go over these, too. 

---

Negative side

1. The singleton pattern is creational.
2. The biggest problem with the singleton pattern is that you assume there will only ever be one instance. This is a big assumption to make and often comes back to bite you. What you end up with is completely inflexible code. 
3. Engineers often use singletons to provide a global access point. They are often used in place of a global variable that has a single instance. But most developers steer clear from global variables, and singletons should provoke the same response. 
4. Singletons leave a trail of confusion
5. They inherently cause code to be tightly coupled. This makes faking them out under test rather difficult in many cases.
6. Singletons are bad when used with multi-threading because with just a single object, the options of threading are limited.
7. Singletons decrease performance.
8. more and more ...

---

Positive side

1. A good standard when choosing to use a singleton or not is when having more than one instance is dangerous. 
2. You need a logistical explanation for locking up the object.

## Other

1. There are three types of design patterns covered by the GoF: creational patterns, structural patterns, and behavioral patterns.

## Reference 

https://dzone.com/articles/singleton-anti-pattern

https://www.contentful.com/blog/2020/05/12/singleton-pattern-evil-or-misused/
