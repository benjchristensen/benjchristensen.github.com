---
author: benjchristensen
comments: true
date: 2007-03-13 16:40:38+00:00
layout: post
slug: double-check-locking
title: Double Check Locking
---

Recently re-visited the double-check-locking pattern (or anti-pattern).

It doesn't work in JDK 1.4 and earlier ... however, in JDK 5, it's updated memory model allows it to be used safely.

[Wikipedia - Double Check Locking
](http://en.wikipedia.org/wiki/Double-checked_locking)

[Sun Blog on JDK 5 and Double Check Locking
](http://blogs.sun.com/cwebster/entry/double_check_locking)

Another possible solution that has the benefit of enforcing compilation ONLY with JDK 1.5 and later is a use of something called AtomicReference.

I haven't played with them yet, but some information can be found at:

[Introduction to Non-Blocking Algorithms](http://www-128.ibm.com/developerworks/java/library/j-jtp04186/)
