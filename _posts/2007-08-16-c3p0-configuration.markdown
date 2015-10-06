---
author: benjchristensen
comments: true
date: 2007-08-16 09:18:11+00:00
layout: post
slug: c3p0-configuration
title: C3P0 Configuration
---

http://www.hibernate.org/214.html

**testConnectionOnCheckout** Must be set in c3p0.properties, C3P0 default: false

Don't use it, this feature is very expensive. If set to true, an operation will be performed at every connection checkout to verify that the connection is valid. A better choice is to verify connections periodically using c3p0.idleConnectionTestPeriod.
