---
author: benjchristensen
comments: true
date: 2008-07-22 05:20:25+00:00
layout: post
slug: uptime-availability
title: Uptime & Availability
wordpress_id: 63
categories:
- Production
---

A good blog entry that I'm pasting below about the cost/benefit of actually achieving 99.999% uptime and how ludicrous it is for most to even attempt let alone claim it.

http://blog.amber.org/2008/07/21/understanding-availability/

With the recent Amazon S3 outage of approximately 8 hours, there’s a lot of people blowing a lot of energy on lambasting Amazon for the downtime. While I think we’d all love to have systems that never go down, the probability of such occurring in the “real world” is relatively small, unless you’re running some esoteric hardware that most people aren’t. Before we go any further, let’s quickly break down what we mean by availability.

When most people talk about availability, they often using the marketing-speak method of speaking in “nines”. Five nines, or 99.999% is the “gold standard” of what most people talk about, but few people actually achieve. To clarify, here’s what it means when you convert percentages to actual time spans.

This means that the vaunted “five nines” allows for only a bit more than five minutes of downtime in a year, and only 6 seconds per week, which translates to less than 1 second per day. Quite honestly, you can’t even bounce an HTTP server in that period of time reliably. For example, if you’re running on a single server, and you have to reboot it more than once a year, you’ll likely never hit 99.99%, even if nothing else breaks.

So what does this mean when we talk about systemic availability? It means that putting all your eggs in one basket—regardless of the quality of the basket—is silly. While many people think about drives failing, and implement RAID or some other technique, and some think about CPU and memory, very few think or plan for electrical system failure or cooling failure. These kind of problems, which strike entire data centers, are not uncommon, and can not be waved away by saying that you have redundant infrastructure.

A vast majority of availability problems, however, are not hardware driven—even though that’s all people think about. They come from a few areas:

- Operator error
- Configuration error
- Software failure/bugs
- Networking
- Power and cooling

All of these cost serious money to solve. They are solved through processes and planning and not just traditional technical operations. In examining failure modes of systems I’ve worked on, a vast majority are preventable. They are due to someone making an unplanned change that isn’t properly vetted. They’re based on software configuration errors, and they’re based on upgrades that simply weren’t tested first.

The silver lining here is this: a vast majority of sites, companies, etc., do not need this kind of availability. The pursuit of high availability tends to be a mental masturbation exercise by people who want to spend money, but aren’t willing to do the cost-benefit analysis. Before undertaking anything above 99.9%, you really need to understand your business to a level that will allow you to make a rational decision about risks. Often, it is cheaper to rebate money to people than it is to fix the problem.

So what do I say to those who puff up and say “I can do better”? I say “no you can’t”. At least, not likely. The cost of running exceptionally high availability systems is not just hardware. It is operational costs. It is staffing, monitoring infrastructure, planning and operational processes. It doesn’t happen when you’ve only got one machine. It doesn’t even happen when you have 50 machines.

Don’t delude yourself any more about your own ability to run systems at that level than you delude yourself into assuming someone else can as well.

