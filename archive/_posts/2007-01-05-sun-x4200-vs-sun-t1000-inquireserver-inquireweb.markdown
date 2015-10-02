---
author: benjchristensen
comments: true
date: 2007-01-05 07:03:00+00:00
layout: post
slug: sun-x4200-vs-sun-t1000-inquireserver-inquireweb
title: Sun x4200 vs Sun T1000 => inQuireServer & inQuireWeb
wordpress_id: 31
categories:
- Performance
---

inQuireServer Tests

A test was done using JMeter using an inQuire Client accessing an inQuire server running on the same local machine.

This is done over JINI using JERI.

Configuration was:
- Catalog: AIDC
- Server Heap: 1GB
- Client Heap: 512MB
- Server JVM: 1.5
- Client JVM: 1.5
- inQuire Build: 4th Jan 07
- Client side caching turned on: Yes

The following image shows the results (times in ms):

[![](http://bp0.blogger.com/_CvV7agFF3Zc/RaKlfxUhp6I/AAAAAAAAACQ/VBstnK8RqIw/s400/t1000-x4200-inquire-server.png)](http://bp0.blogger.com/_CvV7agFF3Zc/RaKlfxUhp6I/AAAAAAAAACQ/VBstnK8RqIw/s1600-h/t1000-x4200-inquire-server.png)
First Test - DC, Keyword and Complex

The T1000 performs very poorly when the thread count is low.

Interestingly however, even though it's gap with the X4200 does reduce, it never gets better, or even close to as good as the X4200.

And surprisingly, it crashes and burns when we try and hit 5000 threads -- a level that is ridiculously slow on the X4200, but at least it runs.

Second Test - DC Only

The second round of tests showed an interesting result -- that the T1000 performs MUCH better when IO intensive tasks are avoided -- such as keyword search which hits the filesystem.

It's still not as good as the X4200 at low thread counts, but much more reasonable -- and does end up scaling better than the X4200.

However, in my opinion, the scale it shows is not nearly superior enough to the X4200 to sacrifice the performance at low or single thread counts, and especially not the lack of Filesystem IO.

inQuireWeb Tests

The next round of testing as against Tomcat running inQuireWeb backed by inQuireServer instances as already tested above.

Client side caching was enabled in inQuireWeb so as to reduce hits to the servers and test Tomcat specifically.

The following image shows how if Tomcat and the inQuireServer were on the same machine, the X4200 was superior, while if Tomcat was on the T1000, and inQuireServer on the X4200, then the T1000 came out on top when it started to scale.

[![](http://bp0.blogger.com/_CvV7agFF3Zc/RaKl0xUhp7I/AAAAAAAAACY/C4k0dvoE_Og/s400/t1000-x4200-inquireweb.png)](http://bp0.blogger.com/_CvV7agFF3Zc/RaKl0xUhp7I/AAAAAAAAACY/C4k0dvoE_Og/s1600-h/t1000-x4200-inquireweb.png)So the conclusion from these tests are that the T1000 does indeed have certain niches where it can perform and scale better than the Opteron based X4200 -- but they are hard to find, and if you don't fit that exact niche, a huge performance hit will be incurred.

At this point, databases and the inQuireServer are out of the questions for the T1000 -- relegating it to a glorifed webserver ... able to host Apache and/or Tomat, as long as the heavy lifting of searches and IO are done elsewhere -- such as on the X4200.

Ben
