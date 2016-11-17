---
layout: post
title: "Hungry Backspace"
category: intellij
tags: [intellij idea, keyboard shortcuts]
date: 2016-11-17
---

How often do you press **backspace multiple times** to get rid of all
**whitespace characters** that are before your cursor?

IntelliJ IDEA has interesting and highly-undocumented editor action called
"Hungry Backspace" that allows you to perform that action with just a one
key press.

![](/images/hungry-backspace/hungry-backspace-with-shortcut.png){:class="img-responsive"}

<!--more-->

By default it doesn't have any keyboard shortcut assigned.
To invoke it you need to press `CTRL` + `SHIFT` + `A`
and type `Hungry Backspace`, which makes it very inconvenient to use.

![](/images/hungry-backspace/hungry-backspace-without-shortcut.png){:class="img-responsive"}

However, a shortcut can be easily added via the Keymap menu.

![](/images/hungry-backspace/hungry-backspace-keymap.png){:class="img-responsive"}

My proposition is to assign `SHIFT` + `BACKSPACE` for this action and override
original behavior which is the same as for just `BACKSPACE`.

![](/images/hungry-backspace/hungry-backspace-assign.png){:class="img-responsive"}

Make a good use of it!
