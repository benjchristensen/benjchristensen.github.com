---
author: benjchristensen
comments: true
date: 2009-06-26 20:29:49+00:00
layout: post
slug: speed-of-thought
title: Speed of Thought
---

I've focused on performance for several years in my server-side and web application development - as much as I've been able to fit into the timelines. It has involved digging into minute details of Java and JVM tuning that rarely get explored by most java developers (from what I can tell anyways) and focusing on tuning the CSS, images, caching, GZIP and other settings of the front-end. It has generally paid off. Today my team operates servers processing millions of complex, dynamic, uncacheable web service transactions completing on average in around 250ms each (server side, not including network transport to client). I believe with further investment we could improve that even more.

I have read comments from companies such as Google and Amazon how the performance of an application can dramatically affect how much people use it. I agree. The slightest friction in searching makes me search less, or shop less, etc.

This past week I've been using the new iPhone 3GS which is at least 2x faster than the previous iPhone 2G I had. In some cases it's 4x and 6x faster.

I already used the iPhone a lot. The increase in speed has further reduced the "friction" of use to the point that if I even have a thought of quickly looking something up or performing some other action, I am much more likely to do it.

On my last iPhone, I consciously chose to not bother at certain times because of the time it would take. Yes, I'm talking in seconds and even milliseconds here -- but when it's a "thought", if the tool doesn't work at the same speed, then it's friction. Same goes for another application I use which involves looking up reference materials and documents. Before I kind of had to avoid "flipping around' while someone was referring to things. It was actually faster to use the paper documents. Now, I can keep up or be faster with my iPhone than the paper version 'users'. Therefore it encourages use.

The new user experience of using the iPhone 3GS, so significantly improved just by the performance improvement, has reminded me as a developer and architect how critical it is to design, plan for and develop to achieve high performance. Functionality isn't enough -- we should be aiming for the "speed of thought".

Interestingly, Google has just launched a new site just for "[speeding up the web](http://code.google.com/speed/)".

The following video shows "the experts" talking about how the human mind perceives changes of 100ms (one tenth of a second).

<iframe width="560" height="315" src="https://www.youtube.com/embed/aXJklICrFJI" frameborder="0" allowfullscreen></iframe>

It's my belief that this isn't just a "nice to have" feature. If a product, service or application wants to be adopted and deemed "necessary" by its users, its performance must reduce friction as much as technically feasible to the point where it approaches or achieves "speed of thought".
