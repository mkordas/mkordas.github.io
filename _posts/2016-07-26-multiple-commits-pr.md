---
layout: post
title: "Your Bugfix Pull Request Should Have Multiple Commits"
category: deveplopment
tags: [pull request, github]
date: 2016-07-26
---

When a code that you wrote is not committed to a repository it effectively does not exist, as it is not visible to anyone besides you.
Moreover, Git doesn't take care of uncommited files and they may simply get lost.
If we commit early and often it's easy to go back to previous state when anything fails.
We can share changes on regular basis and receive feedback about our ideas and architecture. Other people find it easier to integrate and we can avoid merge conflicts.
It's so important to commit early and commit often. Actually it's one of the continuous integration principles.

However, many projects have adopted *only one commit per pull request* rule and they require to squash commits before merging. Here are the reasons:
- commit history is clearer, shorter and more readable
 - serves as documentation
 - explains WHYs which is more important than how exactly change was done and what steps were taken
 - easier to browse from user interfaces without resorting to advanced techniques involving command-line
- repository is leaner and takes less space
- single responsibility principle
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
