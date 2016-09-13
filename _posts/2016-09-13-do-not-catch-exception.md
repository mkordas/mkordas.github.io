---
layout: post
title: "Do Not Catch Exception When Not Necessary"
category: java
tags: [exception, java]
date: 2016-09-13
---

Catching `Excetption` in Java is widely discouraged practice. Checkstyle, PMD, FindBugs - all of these tools have rules complaining
on every attempt to catch `Exception`. While this practice might be useful to do some generic action for all exceptions like logging
and rethrowing with more context, but generally we should stay alert whether it is really necessary.

<!--more-->

Recently I've observed the following piece of code in one of my projects:

{% highlight java %}
try {
    task.perform("");
    fail("Exception was not thrown");
} catch (Exception ex) {
    assertThat(ex, instanceOf(TaskException.class));
    assertThat(((TaskException) ex).getMessages(), contains("Parameter is empty"));
}
{% endhighlight %}

This code verifies that task could not be performed if provided argument is invalid. We expect exception of some particular type
with some specific contents. It doesn't look that bad, does its job, so why bother and listen all static analysis tools that cry
on `catch (Exception ex)` line?

Let's just try rewriting it:

{% highlight java %}
try {
    task.perform("");
    fail("Exception was not thrown");
} catch (TaskException ex) {
    assertThat(ex.getMessages(), contains("Parameter is empty"));
}
{% endhighlight %}

Code becomes shorter, simpler, there are no static-analysis violations anymore.
Behavior stays the same, only assertion message when unexpected exception is throw is going to be different.
Which version do you prefer?
