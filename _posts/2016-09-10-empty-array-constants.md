---
layout: post
title: "Empty Array Constants"
category: java
tags: [java, commons, lang3]
date: 2016-09-10
---

In Java empty arrays (of zero length) are fully immutable and safe to be shared
across entire classloader. This means that if we invoke e.g. `new int[0]` more
 that once that's just waste of memory (very small waste, but still).

<!--more-->

## IDEA Inspection

IntelliJ IDEA has even inspection that searches for such unnecessary object
creation. It's located in `Java | Memory issues | Zero-length array allocation`:

> Reports on allocations of arrays with known lengths of zero. Since array
 lengths in Java are non-modifiable, it is almost always possible to share
 zero-length arrays, rather than repeatedly allocating new zero-length arrays.
 Such sharing may provide useful optimizations in program runtime or footprint.
 Note that this inspection does not report zero-length arrays allocated as
 static final fields, as it is assumed that those arrays are being used to
 implement array sharing.

## Apache Commons to the Rescue

Instead of creating such constants on demand in various location there is
pretty-much industry standard how to obtain them. Very convenient set of empty
arrays is located in `org.apache.commons.lang3.ArrayUtils`.

Note that there is also old `org.apache.commons.lang.ArrayUtils`, but it's the
old API and using it usually is just a mistake or an oversight.

The initial version of them exists since
[2002](https://github.com/apache/commons-lang/commit/d31f3d) and then they were
updated significantly only once in
[2003](https://github.com/apache/commons-lang/commit/2878a4) adding empty arrays
for wrapper types. As you see this implementation is as immutable as themselves.

The full list is as follows:

{% highlight java %}
public static final Object[] EMPTY_OBJECT_ARRAY = new Object[0];
public static final Class<?>[] EMPTY_CLASS_ARRAY = new Class[0];
public static final String[] EMPTY_STRING_ARRAY = new String[0];
public static final long[] EMPTY_LONG_ARRAY = new long[0];
public static final Long[] EMPTY_LONG_OBJECT_ARRAY = new Long[0];
public static final int[] EMPTY_INT_ARRAY = new int[0];
public static final Integer[] EMPTY_INTEGER_OBJECT_ARRAY = new Integer[0];
public static final short[] EMPTY_SHORT_ARRAY = new short[0];
public static final Short[] EMPTY_SHORT_OBJECT_ARRAY = new Short[0];
public static final byte[] EMPTY_BYTE_ARRAY = new byte[0];
public static final Byte[] EMPTY_BYTE_OBJECT_ARRAY = new Byte[0];
public static final double[] EMPTY_DOUBLE_ARRAY = new double[0];
public static final Double[] EMPTY_DOUBLE_OBJECT_ARRAY = new Double[0];
public static final float[] EMPTY_FLOAT_ARRAY = new float[0];
public static final Float[] EMPTY_FLOAT_OBJECT_ARRAY = new Float[0];
public static final boolean[] EMPTY_BOOLEAN_ARRAY = new boolean[0];
public static final Boolean[] EMPTY_BOOLEAN_OBJECT_ARRAY = new Boolean[0];
public static final char[] EMPTY_CHAR_ARRAY = new char[0];
public static final Character[] EMPTY_CHARACTER_OBJECT_ARRAY = new Character[0];
{% endhighlight %}

## Use Them!

Feel free to use them in all your apps that already include `commons-lang3` as
dependency. However, you will still need to cache empty arrays for your custom
types, e.g.:

{% highlight java %}
class Book {
    private static final Book[] EMPTY_BOOK_ARRAY = new Book[0];

    // ...
}
{% endhighlight %}
