---
author: benjchristensen
comments: true
date: 2009-07-07 20:10:33+00:00
layout: post
slug: memory-analyzer-cant-handle-large-heaps
title: Memory Analyzer Can't Handle Large Heaps
wordpress_id: 157
categories:
- Production Problems
- Tools
---

Despite the [claims](http://wiki.eclipse.org/index.php/MemoryAnalyzer/FAQ#Out_of_Memory_Error_while_Running_the_Memory_Analyzer) that [Memory Analyzer](http://www.eclipse.org/mat/) works well with large heaps, the following screenshot is the evidence of my continued inability to have it parse a 3.5GB heap dump.

I have attempted JDK 5 and JDK 6, both 64-bit, with up to 14GB of memory allocated on an 8-core machine with 16GB of memory.

Note the memory bar at the bottom showing it's using only 2121M out of 11879M - yet it still thinks it's running out of memory.

The settings are:


<blockquote>-vmargs

-Xms12g

-Xmx14g

-XX:MaxPermSize=1G

-Dorg.eclipse.swt.internal.carbon.smallFonts

-XstartOnFirstThread</blockquote>


 


-vmargs




-Xms12g




-Xmx14g




-XX:MaxPermSize=1G




-Dorg.eclipse.swt.internal.carbon.smallFonts




-XstartOnFirstThread


 

![Memory Analyzer OutOfMemory](http://benjchristensen.files.wordpress.com/2009/07/picture-1.png)
