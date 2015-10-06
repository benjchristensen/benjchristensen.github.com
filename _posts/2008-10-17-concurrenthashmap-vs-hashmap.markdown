---
author: benjchristensen
comments: true
date: 2008-10-17 20:07:11+00:00
layout: post
slug: concurrenthashmap-vs-hashmap
title: ConcurrentHashMap vs HashMap
---

A simple test of performance for ConcurrentHashMap.

The insert is only a little slower, but the retrieval is 3x slower in this quick and dirty single-threaded test.

 

TimeUtil timer = new TimeUtil();

        timer.start();

        HashMap map = new HashMap();

        for (int i = 0; i < 1000000; i++) {

            map.put(i, i);

        }

        timer.printCurrent();

        

        timer.start();

        ConcurrentHashMap cmap = new ConcurrentHashMap();

        for (int i = 0; i < 1000000; i++) {

            cmap.put(i, i);

        }

        timer.printCurrent();

        

 

        

        timer = new TimeUtil();

        timer.start();

        map = new HashMap();

        for (int i = 0; i < 1000000; i++) {

            map.get(i);

        }

        timer.printCurrent();

        

        timer.start();

        cmap = new ConcurrentHashMap();

        for (int i = 0; i < 1000000; i++) {

            cmap.get(i);

        }

        timer.printCurrent();

 

Action completed in: 458 ms 0.458 seconds

Action completed in: 574 ms 0.574 seconds

Action completed in: 30 ms 0.03 seconds

Action completed in: 113 ms 0.113 seconds
