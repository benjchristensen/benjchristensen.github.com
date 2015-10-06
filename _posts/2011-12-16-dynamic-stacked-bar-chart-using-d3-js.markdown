---
author: benjchristensen
comments: true
date: 2011-12-16 23:03:16+00:00
layout: post
slug: dynamic-stacked-bar-chart-using-d3-js
title: Dynamic Stacked Bar Chart Using d3.js
---

A prototype of a stacked bar chart that can dynamically add/remove bars and update the data for each bar implemented using [d3.js](http://mbostock.github.com/d3/).

It  represents data freshness (time since update) per bar using an opacity decay so a bar fades away if it doesn't receive fresh data.

The examples I [found](http://mbostock.github.com/d3/ex/population.html) [elsewhere](http://mbostock.github.com/d3/ex/stack.html) represent static data, so my model of implementation is different in that I don't use data binding or d3.layout.stack() because I couldn't figure out how to make those work with dynamic data (if someone can show me a better way, I'll gladly accept the guidance). Thus, my implementation directly adds/removes the bars and determines the bar widths and x-position itself.

The use case I intend to apply this prototype for is to visualize a stream of realtime data.

Functionality not implemented in this prototype include things such as hover and click actions to show details of the data a bar represents.

![](http://benjchristensen.files.wordpress.com/2011/12/barchart.png?w=615)

Here are links to the code and working example:

[http://bl.ocks.org/1488375](http://bl.ocks.org/1488375)
[ https://gist.github.com/1488375](https://gist.github.com/1488375)
