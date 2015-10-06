---
author: benjchristensen
comments: true
date: 2012-11-27 04:33:56+00:00
layout: post
slug: hystrix-for-resilience-engineering
title: Hystrix for Resilience Engineering
---

Today Hystrix was released on GitHub at [http://github.com/Netflix/Hystrix](http://github.com/Netflix/Hystrix).

It is a latency and fault tolerance library used for resilience engineering and something I have spent a good chunk of time on at Netflix. I'm happy to see it get released as open-source and be able to continue evolving it (hopefully with community involvement).

As written originally for the [Netflix Tech Blog](http://techblog.netflix.com/2012/11/hystrix.html):



<blockquote>In a distributed environment, failure of any given service is inevitable. Hystrix is a library designed to control the interactions between these distributed services providing greater tolerance of latency and failure. Hystrix does this by isolating points of access between the services, stopping cascading failures across them, and providing fallback options, all of which improve the system's overall resiliency.

Hystrix evolved out of resilience engineering work that the Netflix API team began in 2011. Over the course of 2012, Hystrix continued to evolve and mature, eventually leading to adoption across many teams within Netflix. Today tens of billions of thread-isolated and hundreds of billions of semaphore-isolated calls are executed via Hystrix every day at Netflix and a dramatic improvement in uptime and resilience has been achieved through its use.</blockquote>



![](http://benjchristensen.files.wordpress.com/2012/11/hystrix-logo-tagline-vertical.png)
