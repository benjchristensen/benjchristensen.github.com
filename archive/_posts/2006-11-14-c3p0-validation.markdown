---
author: benjchristensen
comments: true
date: 2006-11-14 07:53:00+00:00
layout: post
slug: c3p0-validation
title: C3P0 Validation
wordpress_id: 22
categories:
- Code
---

We were getting random broken connections ... the following properties got rid of them.

c3p0.testConnectionOnCheckout=true
c3p0.preferredTestQuery=select 1

See [Adnan's site](http://adnanm.blogspot.com/2007/07/monitoring-c3p0-using-jmxjconsole.html) for more information on C3P0.
