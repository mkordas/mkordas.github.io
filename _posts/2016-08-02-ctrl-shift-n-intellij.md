---
layout: post
title: "The power of CTRL + SHIFT + N in IntelliJ IDEA"
category: intellij
tags: [intellij idea, keyboard shortcuts]
date: 2016-08-02
---

IntelliJ IDEA has many useful navigation features. Every competent user already
 knows, that in order to navigate to any file in the project it's enough to
 press `CTLR` + `SHIFT` + `N` and type file name or its part. Nevertheless,
 we usually use this functionality in very limited way.

<!--more-->

First of all, we don't need to type full file name. If we search for
 `ProblemFactory`, the following searches will work:

- `ProFact`
- `PF`

Actually this search window is not case sensitive. It analyzes search string and
 just tries to match them with prefixes of camelCase names, so the following is
 also fine:

- `profact`
- `pf`
- `pfactory`
- `factory`

Actually, you don't need any uppercase letters in this search window. They don't
 help with anything. So why bother to press `SHIFT`?

Search results contain very nice highlighting of matched characters.

However, if the search string cannot be matched literally with the prefixes,
 we won't get any results:

- `ProFtory`
- `prblmfctr`

This is when `*` wildcard becomes very useful:

- `ProF*tory`
- `pr*bl*mf*ct*r`

Have you noticed two different colors in the results? Tests always are displayed
 in greed background, unless you disable that feature with `File Colors enabled`
 toggle.

This search feature has also possibility to navigate to certain
 directories/packages. It's enough to follow the name with `/`. All previous
 rules apply, so to open directory `problematic` you can use the following:

- `problema/`
- `pr*bl*m*tic/`

Looking for a file withing a certain directory path? Just separate
 queries for each directory and file name with space. Let's say we're interested
 in all the files that are contained somewhere within `src`, `michalkordas`,
 `intellij` directories, having initials `pf` and extension `.java`. Here's the
 search phrase:

    src/ michalkordas/ intellij/ pf .java

So easy!

It's also possible to navigate through history of searches with `CTRL` +
 `UP` / `DOWN`.

In IntelliJ pressing some shortcut twice always means "give me more". In this
 context, when `CTLR` + `SHIFT` + `N` is pressed twice, we can search in all
 indexed locations, including all libraries. Interested in all `Factory` classes
 you have on classpath? Just press shortcut again. You can also toggle with
 `ALT` + `N`.

We can also filter files by types. I find it useful, when e.g I'd like to list
 all XML files, even if they have different extensions (XML file
 type is attached to multiple extensions). Then I just type query, it can even
 be a `*` to list all `.xml`, `.xsd` and others in the indexed locations.
