---
author: benjchristensen
comments: true
date: 2006-11-14 07:56:00+00:00
layout: post
slug: performance-optimizations
title: WebApp Performance Optimizations
---

Playing around with real-world performance optimizations found JSMin to work quite well ... and very big gains by doing the following:

- combining multiple Javascript files into a single file
- using a JSMin servlet filter to minimize and cache in memory the Javascript file to return
- adding a filter to add HTTP Header caching to static files
- reducing file sizes for product images
