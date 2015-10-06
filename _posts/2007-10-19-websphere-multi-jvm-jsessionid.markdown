---
author: benjchristensen
comments: true
date: 2007-10-19 22:30:36+00:00
layout: post
slug: websphere-multi-jvm-jsessionid
title: Websphere Multi-JVM jsessionid
---

Works just like it should :-)

[IBM Support Link](http://www-1.ibm.com/support/docview.wss?rs=180&context=SSEQTP&dc=DB520&uid=swg21210881&loc=en_US&cs=UTF-8&lang=en&rss=ct180websphere)

Two JVMs with different contexts but the same domain now use the same jsessionid so they can talk back and forth in the same browser without jsessionid schizophrenia.
