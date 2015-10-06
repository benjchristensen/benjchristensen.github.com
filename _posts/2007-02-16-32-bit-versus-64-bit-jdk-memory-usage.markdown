---
author: benjchristensen
comments: true
date: 2007-02-16 21:06:00+00:00
layout: post
slug: 32-bit-versus-64-bit-jdk-memory-usage
title: 32-bit versus 64-bit JDK Memory Usage
wordpress_id: 33
categories:
- Code
- Performance
---

Summary of analysis performed September 2006.

Testing Strategy

To ensure the tests performed were reliable and behaved the same every time with as few variables as possible, a simple program (a single java class) was written which loops indefinitely, adding objects to a collection until it runs out of memory.

This test was performed with both Integer and String objects, and then executed with 3 different JVMs with varying heap settings.

The results and details of these tests are documented in later chapters.

JVMs tested:
- JDK 1.4.2 32-bit
- JDK 1.5 32-bit
- JDK 1.5 64-bit

Operating Systems Tested
- Solaris 10 on Opterons
- Suse Linux 10 on Opterons

The tests are far from exhaustive, but were enough to derive numbers and patterns whereby the JVMs can be sized accurately and recommendations made.

Findings

- Tests performed consistently on both Linux and Solaris (except for maximum heap sizes)
- JDK 5 64-bit takes between 40% - 50% more memory on average than either 32-bit JVM
- JDK 1.4 32-bit is slightly more memory efficient than JDK 5 32-bit
o It is slightly better than JDK 5 32-bit in Integer tests
o It is exactly the same as JDK 5 32-bit in String tests

- Solaris 10 can run a 32-bit JVM up to 3.5GB
- Suse Linux can run a 32-bit JVM up to 2GB
- A 64-bit JVM was successfully run at 20GB on Suse Linux
- A 2GB 32-bit JVM is approximately equivalent to a 3GB 64-bit JVM in number of objects stored
o ie. On Suse Linux, if more than 2GB heap is needed, then one must jump to a 3GB 64-bit JVM to achieve the same amount of storage
o ie. On Solaris, if more than 3.5GB heap is needed, then one must jump to a 5GB 64-bit JVM to achieve the same amount of storage

Recommendations

Based upon these findings, it is recommended that JDK 5 32-bit be used as the default JVM, and 64-bit used if more memory is needed than what can be allocated to a 32-bit JVM with the understanding of the ratio one must increase to account for the change to a 64-bit data model.

The reasons for choosing JDK 5 over JDK 1.4 are:

- JDK 5 is the current recommended production JVM from Sun Microsystems
o It has been out for more than 2 years and is at its 8th maintenance release (JDK 1.5_08)

- General performance improvements from JDK 1.4 to JDK 5
o http://java.sun.com/j2se/1.5.0/docs/guide/performance/speed.html
o http://java.sun.com/j2se/1.5.0/docs/guide/vm/index.html

- Improved garbage collection algorithms, particularly for multi-processor machines
o http://java.sun.com/docs/hotspot/gc5.0/gc_tuning_5.html

- 64-bit JVM available on AMD Opterons when larger heap sizes required (not available for JDK 1.4)
o http://java.sun.com/j2se/1.5.0/docs/relnotes/features.html#platform_proc64

Summary

The tests performed confirmed that the 64-bit JVM does indeed use more memory than the 32-bit JVMs, but that it behaves consistently and can be calculated, and therefore planned for.
It is recommended to use JDK 5 32-bit as the default JVM, and the 64-bit variant when larger heap sizes are required.

Java Source File: [MemoryTest.java](http://benjchristensen.files.wordpress.com/2007/04/memorytestjava.doc)
