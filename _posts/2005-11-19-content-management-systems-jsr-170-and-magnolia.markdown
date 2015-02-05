---
author: benjchristensen
comments: true
date: 2005-11-19 21:14:00+00:00
layout: post
slug: content-management-systems-jsr-170-and-magnolia
title: Content Management Systems -- JSR 170 and Magnolia
wordpress_id: 5
categories:
- Architecture
- Code
---

In the past week I've done a bunch of research on content management systems, and in particular the Java standard JSR 170.

I've been playing with Magnolia and so far am fairly impressed with how it works -- though not so impressed with the backend repository which in this case is JackRabbit, the open source reference implementation.

It appears though that for a fairly reasonable price I can get the Enterprise version of Magnolia that uses the commercial JSR-170 compliant repository from Day (http://www.day.com/site/en/index.html). It sounds like it should be MUCH better ... and is very likely what all the big name companies use that Magnolia lists on their site. I've requested them to contact me but haven't heard back yet.

JSR-170 definitely is sounding nice ... though it seems like it still has a way to go before it fully matures as it's quite new.

Also, the opensource community obviously has not had enough time to make a decent enterprise implementation, as Jackrabbit doesn't cut it. For example ... I have the system running with JackRabbit ... it only support filesystem persistence right now, so I try to connect another client to it and .... it doesn't work ( the files are locked) .... so that means it won't work so well except for small things.

Also, I see no nice way of connecting remotely to the repository using the open source version of Magnolia.

I'll continue researching this in the coming week.
