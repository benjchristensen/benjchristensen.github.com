---
author: benjchristensen
comments: true
date: 2011-08-09 05:52:24+00:00
layout: post
slug: simple-sparkline-using-svg-path-and-d3-js
title: Simple Sparkline using SVG Path and D3.js
wordpress_id: 388
categories:
- Code
- User Interface
---

I've been playing with SVG visualization and the [d3.js](http://mbostock.github.com/d3/) library (replacement to [Protovis](http://mbostock.github.com/protovis/)).

As a starting point this is a simple line chart used as a sparkline. The HTML and Javascript provide a boiler plate from which more complex visualizations and charts can be built.

![](http://benjchristensen.files.wordpress.com/2011/08/screen-shot-2011-08-08-at-10-47-16-pm.png?w=800)

Here are links to the code and working example:

[http://bl.ocks.org/1133472](http://bl.ocks.org/1133472)
[ https://gist.github.com/1133472](https://gist.github.com/1133472)

To make the size more applicable to inline ![](http://benjchristensen.files.wordpress.com/2011/08/screen-shot-2011-08-08-at-11-00-18-pm.png?w=800) use as a sparkline decrease the ranges:
`
var x = d3.scale.linear().domain([0, 10]).range([0, 20]);
var y = d3.scale.linear().domain([0, 10]).range([0, 10]);
`



UPDATE: I added another version that shows animations with transformations and transitions.

[http://bl.ocks.org/1148374](http://bl.ocks.org/1148374)
[https://gist.github.com/1148374](https://gist.github.com/1148374)
