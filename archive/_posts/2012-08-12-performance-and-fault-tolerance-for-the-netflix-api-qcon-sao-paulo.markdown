---
author: benjchristensen
comments: true
date: 2012-08-12 22:24:02+00:00
layout: post
slug: performance-and-fault-tolerance-for-the-netflix-api-qcon-sao-paulo
title: Performance and Fault Tolerance for the Netflix API - QCon Sao Paulo
wordpress_id: 504
categories:
- Architecture
- Code
- Performance
- Production
---

A presentation I gave at QCon Sao Paulo on August 4th 2012 (http://qconsp.com/palestrante/ben-christensen)

**Presentation Description**

The Netflix API receives over a billion requests a day which translates into multiple billions of calls to underlying systems in the Netflix service-oriented architecture. These requests come from more than 800 different devices ranging from gaming consoles like the PS3, XBox and Wii to set-top boxes, TVs and mobile devices such as Android and iOS.

This presentation describes how the Netflix API supports those devices and achieves fault tolerance in a distributed architecture while depending on dozens of systems which can fail at any time. It also explains how a new system design allows each device to optimize API calls to their unique needs and leverage concurrency on the server-side to improve their performance.

(Some slides have been modified and notes included for readability and understanding of content without accompanying speech.)


[slideshare id=13927636&doc=faulttolerancepresentation-qcon-sao-paulo-august2012-120809145821-phpapp02]




Slides also available at [SpeakerDeck](https://speakerdeck.com/u/benjchristensen/p/performance-and-fault-tolerance-for-the-netflix-api-qcon-sao-paulo).




![](http://benjchristensen.files.wordpress.com/2012/08/azdpfe3cyaacgwb.jpg)




![](http://benjchristensen.files.wordpress.com/2012/08/azdmroxcyaey4hz.jpg)




[Conference center on Google Maps](https://maps.google.com/maps?q=%22Federacao+Comercio+Estado+Sao+Paulo%22,+S%C3%A3o+Paulo,+Brazil&hl=en&ie=UTF8&ll=-23.557654,-46.652498&spn=0.030999,0.065103&sll=-23.558425,-46.653431&sspn=0.041384,0.07699&hq=%22Federacao+Comercio+Estado+Sao+Paulo%22,&hnear=Sao+Paulo+-+S%C3%A3o+Paulo,+Brazil&t=m&z=15&layer=c&cbll=-23.557616,-46.652401&panoid=FGfV2pbo0UZi3fgLfQOSgQ&cbp=12,145.88,,0,-4.96)
