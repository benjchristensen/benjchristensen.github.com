---
author: benjchristensen
comments: true
date: 2007-01-02 07:06:00+00:00
layout: post
slug: sun-x4200-vs-sun-t1000-load-server
title: Sun x4200 vs Sun T1000 => Load Server
---

Testing the Sun T1000 and Sun X4200 continues ...

... with the databases loaded, I'm now starting the inQuire Server with various types of configuration involving indexing in MEMORY, FILESYSTEM or DATABASE.

I understand that these processes are still primarily single-threaded ... but I'm so far not very impressed by the T1000.

If it takes 7+ times longer to initialize a process before I can even get to a point where parallel processing can occur, it's questionable if it's worth it.

And ... the inQuire Keyword FILESYSTEM implementation is really slow and needs to be replaced.

[
](http://bp1.blogger.com/_CvV7agFF3Zc/RZoE59x2RNI/AAAAAAAAABs/a_b6ioJyZX4/s1600-h/t1000vsx4200-load.png)[![](http://bp1.blogger.com/_CvV7agFF3Zc/RaKf4BUhp5I/AAAAAAAAACE/RvKnopcAJo0/s400/t1000-x4200-load.png)](http://bp1.blogger.com/_CvV7agFF3Zc/RaKf4BUhp5I/AAAAAAAAACE/RvKnopcAJo0/s1600-h/t1000-x4200-load.png)
