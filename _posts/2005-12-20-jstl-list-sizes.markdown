---
author: benjchristensen
comments: true
date: 2005-12-20 06:32:00+00:00
layout: post
slug: jstl-list-sizes
title: 'JSTL: List Sizes'
wordpress_id: 6
categories:
- Code
---

This link is useful for getting list sizes etc using JSTL:

http://forum.java.sun.com/thread.jspa?threadID=484828&messageID=3731101

Here is the piece for testing a certain size:

<c:**if** test="${osms[1] ne null}">

And if using JSTL 1.1 to get the size:

<c:**if** test="${fn:length(list) > 1}">
