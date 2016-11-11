---
layout: post
title: "The Quickest Way to Introduce Variable in IntelliJ IDEA"
category: intellij
tags: [intellij, idea]
date: 2016-07-11
---

Many coders consider themselves as smart when they have learnt how to use `CTLR`
\+ `SPACE`. When they need to declare variable
{% highlight java %}
final List<Object> list = new ArrayList<>();
{% endhighlight %}
they press `CTRL` + `SPACE` to complete each word separately, which gives about
5-6 autocompletions and decent amount of typing for the above.

Let me teach you the trick that would save you thousands of keypresses in your
life. Just type `new ArLi`, press `CTRL` + `ALT` + `V` and... you are done!

<!--more-->

If you try to use it for a first time, you will notice that variable is not
`final`. To add it, just press `ALT` + `F`. You may also get `ArrayList` type,
which is obviously bad thing ("Code to the interface!"). Fixing it is also
simple. Press `SHIFT` + `TAB`, and choose `List` from the list.

There's also one more enhancement you can apply. Maybe you've noticed that
typing `new ArLi` works just fine, but it doesn't for `new Arli` or `new arli`.
To include these cases find with `CTRL` + `ALT` + `A` a setting called
`Case sensitive completion:` and set it to `None`.

Want more excitement? This trick works also for:

- declaring fields - `CTRL` + `ALT` + `F`
- declaring constants -  `CTRL` + `ALT` + `C`
- wrapping object with a method (!) - magic happens on `CTRL` + `ALT` + `M`
