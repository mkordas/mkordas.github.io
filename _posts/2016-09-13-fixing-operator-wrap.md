---
layout: post
title: "Fixing OperatorWrap Violations"
category: checkstyle
tags: [intellij idea]
date: 2016-09-13
---

According to [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html), section
[Where to break](https://google.github.io/styleguide/javaguide.html#s4.5.1-line-wrapping-where-to-break) all lines
should be broken before non-assignments operators. 

Unfortunately, IntelliJ IDEA by default leaves the operators at the end of line...

<!--more-->

It happens when generating `toString` method using `String concat (+)` template

{% highlight java %}
    @Override
    public String toString() {
        return "OperatorWrap{" +
                "operator='" + operator + '\'' +
                ", wrap='" + wrap + '\'' +
                '}';
    }
{% endhighlight %}

And also when breaking a string, e.g. with:

{% highlight java %}
    return "OperatorWrap";
{% endhighlight %}    

when enter is pressed after `Operator`it becomes:

{% highlight java %}
    return "Operator" +
        "Wrap";
{% endhighlight %}

Checkstyle detects such code with
[`OperatorWrap`](http://checkstyle.sourceforge.net/config_whitespace.html#OperatorWrap) check. All good, build is going
to fail, but how to fix these violations efficiently? Sadly, IDEA does not offer any quick-fix intention for that.

Actually, it's very easy to fix these violations with good old regex search and replace. Just search for

    \+\s*\n(\s+)
  
and replace these occurences with (note space at the end):

    \n$1+ 

Hopefully it will be working for you as good as it works for me.
