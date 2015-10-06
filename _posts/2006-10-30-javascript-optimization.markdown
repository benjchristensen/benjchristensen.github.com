---
author: benjchristensen
comments: true
date: 2006-10-30 19:18:00+00:00
layout: post
slug: javascript-optimization
title: Javascript optimization?
---

From what I can tell ... the best bets are:

Use this to minimize file size: http://alex.dojotoolkit.org/shrinksafe/

Then enabled mod_deflate rather than mod_gzip

... make sure Apache is doing compression in memory, and not on the filesystem.

Then, actually change JS and CSS filenames each time they change so we can forcefully set very long cache refresh times so they never expire.
