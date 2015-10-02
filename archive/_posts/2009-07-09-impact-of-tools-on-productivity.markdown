---
author: benjchristensen
comments: true
date: 2009-07-09 01:22:50+00:00
layout: post
slug: impact-of-tools-on-productivity
title: Impact of Tools on Productivity
wordpress_id: 173
categories:
- Tools
---

Yesterday I was [analyzing java heap dumps](http://benjchristensen.com/2009/07/07/netbeans-heap-profiler-works-well/) at my office using a Mac Pro with 8 Xeon CPU cores and 16GB of memory.

It took 30-60 seconds to load a 3.5GB file and was very usable while browsing the heap and analyzing it.

When I got home I wanted to peruse it a little more. I just had my laptop, a MacBook Pro with a Core 2 Duo 2.5GHz and 4GB memory.

It took over 20 minutes just to load the file, and the machine was virtually unusable that entire time. Once loaded, every click of the mouse took time ranging from a noticeable lag to multiple seconds of being hung. The machine was swapping to death. Even though I have a very high end laptop, it just couldn't handle what I was throwing at it as compared to the very powerful desktop machine.

I gave up rather quickly as the [friction](http://benjchristensen.com/2009/06/26/speed-of-thought/) of using the system was too high. I didn't have the patience to deal with it - I just waited until I returned to the office today and again used the Mac Pro.

It has made me think again about what kind of equipment is provided to development teams. I know for a fact that my extended team of 40+ overseas don't have a single machine in their office as powerful as the Mac Pro I was using.

So, if one of them needed to analyze that heap dump, profile a large server application or do some other intensive task, what would they do? Deal with 20 minute waits as opposed to 30 seconds, and multi-second pauses between each mouse click - and waste a day in their effort instead of minutes or hours of effective work allowing their tools to work as fast as their thoughts?

One could argue that a remote server, such as one at EC2 could be used for a couple hours by using a web based solution like JHat to analyze the heap. Except that [didn't work](http://twitter.com/benjchristensen/status/2534093699) so well.

How much productivity is lost because a developer is given equipment below actual requirements, or by making them use the same machine long past its usefulness (3 years is an eternity for a developer, yet is a standard 'depreciation' time for which a developer is often made to endure their machine).

For example, I have 4GB on my laptop and push on that limit constantly. Yet I know a lot of my team only has 2GB, and are working on CPU architectures several years old.

For a US developer this is just silly - as having new equipment every 18-24 months is a fraction of the cost of the persons salary, and in my opinion more than makes up for itself in improved productivity as well as morale.

For an offshore developer, with much lower salary costs it's a higher fraction, but still I believe its dividends are worth it.

This applies to all types of tools and equipment for developers: faster machines, more memory, [dual large monitors](http://martinfowler.com/bliki/BigScreen.html), commercial software as opposed to everything being opensource and other such things.

People are expensive. I think it's more cost effective to spend a little on the right equipment and increase productivity and morale of development teams by giving them the right tools - as I had while analyzing heap dumps.
