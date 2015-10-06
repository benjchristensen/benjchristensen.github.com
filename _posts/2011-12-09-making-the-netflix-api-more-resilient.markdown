---
author: benjchristensen
comments: true
date: 2011-12-09 17:57:17+00:00
layout: post
slug: making-the-netflix-api-more-resilient
title: Making the Netflix API More Resilient
---

A new [Netflix Tech Blog post](http://techblog.netflix.com/2011/12/making-netflix-api-more-resilient.html) by my manager ([Ben Schmaus](https://twitter.com/#!/schmaus)) discusses how we've been making the Netflix API more resilient through the use of circuit breakers, bounded thread-pools and realtime decision making:


<blockquote>Here are some of the key principles that informed our thinking as we set out to make the API more resilient.

> 
> 
	
>   1. A failure in a service dependency should not break the user experience for members
> 
	
>   2. The API should automatically take corrective action when one of its service dependencies fails
> 
	
>   3. The API should be able to show us what’s happening right now, in addition to what was happening 15-30 minutes ago, yesterday, last week, etc.
> 

</blockquote>


A video showing the realtime monitoring dashboard is on Vimeo:

<iframe src="https://player.vimeo.com/video/33576628" width="500" height="275" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe> <p><a href="https://vimeo.com/33576628">Netflix API Circuit Dashboard</a> from <a href="https://vimeo.com/benjchristensen">Ben Christensen</a> on <a href="https://vimeo.com">Vimeo</a>.</p>
