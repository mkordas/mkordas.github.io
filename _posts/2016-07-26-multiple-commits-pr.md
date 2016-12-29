---
layout: post
title: "Your Bugfix Pull Request Should Have Multiple Commits"
category: deveplopment
tags: [pull request, github]
date: 2016-07-26
---

When a code that you wrote is not committed to a repository, it effectively doesn't exist, as it is not visible to anyone besides you.
Moreover, Git doesn't take care of uncommitted files and they may irrecoverably get lost.
If we commit often it's easy to go back to previous state when anything fails.
We can share changes on regular basis and receive timely feedback about our ideas and architecture of a solution.
Other people know what is going on. There are less merge conflicts and less duplicated work.
Exact statuses are shared even before stand-up meetings.
All of the above are the basic continuous integration principles and we cannot say we have proper CI when people have uncommitted changes hanging out for days.

![](/images/rails.jpg){:class="img-responsive"}

<!--more-->

If it looks like the rule is to **commit early and often** we quickly end up with dozens of commits for relatively easy changes in our GitHub pull requests. 
It enables us to track the progress, see the chosen development path and review only the new stuff that was added instead of reviewing again and again the entire change.

Perhaps in the contrary to the above, many projects have adopted **only one commit per pull request** rule and they require to always squash commits.
The main reason for that is to have short, clear and readable history of all significant changes that serves as project documentation.
Idea is that such history explains better all the WHYs which are much more important than HOW exactly change was done and what steps were taken.
Simple history is easier to browse and comprehend from user interfaces (like GitHub) without resorting to advanced techniques involving command-line.
When a project is huge, having leaner and smaller repository will also be more performant for all the contributors.
Lastly, we can apply single responsibility principle in various contexts, even for pull request.
This means that they should be focusing only on one concern and doing it great.

Generally the above convinces me and I squash commits. I used to do it always, even during development, with `git commit --amend` and `git push --force`.
Now I see that this is not ideal and there are many exceptions.

For me couple of well-made commits may significantly simplify review and make history even clearer in **some specific cases**, especially
for non-trivial bugfixes or features that should be verified on system/integration level.

Squashed commits:

1. Test, bugfix and refactoring **mixed together**

Sample solution with 3 commits:

1. **Test** that reproduces bug on system/integration level. For this commit build should **fail for the proper reason**, and should
 have red tick in GitHub
2. Simplest possible **bugfix** so that no one has any doubts where the bug was, should have already green tick on GitHub
3. Minimal **refactoring** needed to pass code review, additional refactoring can be done in other PRs before/after

 Ideally, responsible code reviewer should make sure that the test added really reproduces the bug and fails for the proper reason.
 It is **too easy to create test that passes always**, even if it was failing initially. Having commit with just a test can be an
 **evidence** for a reviewer that throughout changes to PR this test is still failing, and enables to easily **verify assertion/error
 message** (which is also very important!).

Moreover, commit with just a bugfix makes immediately obvious what was the real functional problem. It is not lost in between
refactoring or other not-related changes and can be reviewed separately with a greater care.


Of course, you can still squash commits just before merge if reasonable. 
GitHub recently even introduced the "Confirm squash and merge" button that allows to preserve development commits, but only one squashed commit with adjusted title and description goes to the master branch.

So do not follow the rules to make just one or many commits per PR blindly and always choose the sweet spot.

