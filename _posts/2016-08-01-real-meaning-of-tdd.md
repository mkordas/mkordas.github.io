---
layout: post
title: "The Real Meaning of TDD"
category: deveplopment
tags: [tdd, test-driven development]
date: 2016-08-01
---

As with majority of conceptions in software development, their original meaning
gets obscured pretty fast. I have impression that it happened even to as simple
idea as TDD...

During interviews I like to ask simple question: How do you understand TDD?
I'm so surprised by some of the answers...

* "project has some tests"
* "code coverage is at least 80%"
* "tests are written during the same iteration"

More educated guys notice that it's about the order:

* "all tests should be written first"
* "tests should be created after initial skeleton of application"

Very few of them understand the actual essence of TDD. There's no one definition
what it is, but I'd be more than satisfied with the following explanations:

* It's a practice where all the code and entire design is driven by having a
  test first
* It's a practice consisting of three steps that can be applied on any level of
  software project:
  1. Think about scenario. Write minimal test with proper name or extend
     existing one. Make sure that test fails for the proper reason.
  2. Write minimal amount of code that makes test passing. Do not worry about
     design and duplication. Afterwards you should also change new
     implementation a bit and see that test fails again.
  3. Get rid of all duplication introduced. Observe that test is passing all the
     time. Do a really heavy refactoring having in mind that is time, when your
     entire design emerges.
