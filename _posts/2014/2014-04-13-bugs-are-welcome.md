---
layout: article
title: "Bugs Are Welcome"
date: 2014-04-13
author:
  name: Yegor Bugayenko
  avatar: http://www.gravatar.com/avatar/70942ffdd8084b5a51e17e3c0996d53c?s=300
categories: blog
disqus: true
tags:
  - bugs
  - process
  - principles
description: |
  Unlike a very common understanding of a software bug as something negative,
  XDSD encourages all team members to find and report as many bugs
  as possible, in order to improve quality of the end product
keywords:
  - defects planning
  - management of programmers
  - software testing
  - test planning
  - test plan
  - test script
---

The traditional understanding of a software defect (aka "bug") is that it is
something negative and want to avoid in our projects. We want our projects to be
"bug-free." Our customers are asking us to develop software that doesn't have
bugs. And, we, as users, expect software to work without bugs.

{% picture http://img.xdsd.org/2014/04/charlie-and-chocolate-factory-chewing-breakfast.jpg 0 Charlie and the Chocolate Factory (2005) by Tim Burton %}

But, let's take a look at bugs from a different angle. In XDSD, we say that
"bugs are welcome." This means we encourage all interested parties to find bugs
and report them. We want our team to see bugs as something that we need in our
projects. Why?

Because we understand that there are two categories of bugs: visible and hidden.
The more bugs that become visible, the more of them we can fix. More fixed bugs
means fewer to annoy our users. By discovering bugs we make them visible.

This is the primary job of a software tester &mdash; to make bugs visible.

Obviously, their visibility affects the quality of the product in a positive
way. This is because we can fix them before our users start complaining.

In order to motivate all team members to make more bugs visible, we pay for
their discovery. In XDSD projects, we are pay 15 minutes for every bug found (no
matter who finds them and where.)

## We Plan Bugs

We go even further. At XDSD, we plan for a number of hidden bugs in every
project. We do this by using our experience with previous projects and expert
judgment.

Let's say we're starting to develop a web system, which is similar to the one we
worked on last year. We know that in the previous project our users and team
together reported 500 bugs.

It's logical to assume that the new project will have a similar number of bugs.
Thus, our task is to make those 500 bugs visible before they hit the production
platform and our users call us to complain about them. Therefore, we're making
it one of the project goals: "discover 500 bugs."

Of course, our estimate may be wrong. Nevertheless, we have historical records
for a few dozen projects, and in all of them the number is close to 500. So,
finding 500 bugs in a project is usually a reality &mdash; we can use it as a
target.

## What Is a Bug?

Let us try to define a bug (or software defect) in a non-ambiguous manner.
Something can be reported as a bug and subsequently paid for iff:

 * it is [reproducible](http://en.wikipedia.org/wiki/Reproducibility)
 * it refers to functionality already implemented
 * is can be fixed in a reasonable amount of time
 * it doesn't duplicate a bug already reported

Reproducibility of a bug is very important. Consequently, it is the
responsibility of a bug reporter to make sure the bug is reproducible. Until it
is proven that the bug can be reproduced &mdash; it's not a bug for which
payment can be made.

A bug is not a task; it has to refer to an existing functionality. Additionally,
an explanation must exist for how and when the existing functionality doesn't
work as expected.
