---
author: benjchristensen
comments: true
date: 2007-01-02 02:03:00+00:00
layout: post
slug: sun-x4200-vs-sun-t1000-importing-content
title: Sun x4200 vs Sun T1000 => Importing Content
---

Here are some numbers showing performance of our inQuire Importer against a MySQL 5.x database using our IT North American catalog with 500k+ products.

Basically it seems the T1000 is HORRIBLE for this type of application.

Of it's 32 available CPU cores, generally only 1 of them is being used during these processes -- when multiprocessing maybe 4 or 5 of them.

The X4200 basically ends up being 7x faster than the T1000.

Next tests are using Tomcat on the T1000 to try it's multiprocessing.

[![](http://bp2.blogger.com/_CvV7agFF3Zc/RZm-kdx2RMI/AAAAAAAAABc/R_EJA6xG9N4/s400/t1000vsx4200-imports.png)](http://bp2.blogger.com/_CvV7agFF3Zc/RZm-kdx2RMI/AAAAAAAAABc/R_EJA6xG9N4/s1600-h/t1000vsx4200-imports.png)
