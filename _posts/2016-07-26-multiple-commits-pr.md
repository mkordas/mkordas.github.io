---
layout: post
title: "Your Bugfix Pull Request Should Have Multiple Commits"
category: deveplopment
tags: [pull request, github]
date: 2016-07-26
---

Many projects have adopted *only one commit per pull request* rule. It makes commit history much more [clear and readable](http://programmers.stackexchange.com/questions/263164/why-squash-git-commits-for-pull-requests).
Generally I agree with it, but I'd like to propose an exception from this rule.

![](/images/rails.jpg){:class="img-responsive"}

<!--more-->

For me couple of commits may significantly simplify review and make history even clearer in **some specific cases**, especially
for non-trivial
bugfixes or features that should be verified on system/integration level.

Squashed commits:

1. Test, bugfix and refactoring **mixed together**

Sample solution with 3 commits:

1. **Test** that reproduces bug on system/integration level. For this commit build should **fail for the proper reason**, and should
 have red tick on GitHub
2. Simplest possible **bugfix** so that no one has any doubts where the bug was, should have already green tick on GitHub
3. Minimal **refactoring** needed to pass code review, additional refactoring can be done in other PRs before/after

 Ideally, responsible code reviewer should make sure that the test added really reproduces the bug and fails for the proper reason.
 It is **too easy to create test that passes always**, even if it was failing initially. Having commit with just a test can be an
 **evidence** for a reviewer that throughout changes to PR this test is still failing, and enables to easily **verify assertion/error
 message** (which is also very important!).

Moreover, commit with just a bugfix makes immediately obvious what was the real functional problem. It is not lost in between
refactoring or other not-related changes and can be reviewed separately with a greater care.

So do not follow the rule to make just one commit per PR blindly and always choose sweet spot of the number of commits.
