---
author: benjchristensen
comments: true
date: 2007-10-14 06:12:25+00:00
layout: post
slug: lessons-learned
title: Lessons Learned
---

[1] Don't be accommodating to a client ... otherwise, when all hell breaks loose none of that will matter and any issues resulting from attempts to accommodate last minute changes, bad decisions and architecture/environmental issues will all be the fault of the development team -- instead of the client.

[2] If one wants to be accommodating, then everything must be done so with disclaimers in writing to significantly high enough ranking people -- Director or VP -- managers don't cut it.

[3] Dictate every single aspect of an environments requirements and thresholds, even if it's not directly related to the application and even (especially?!) if it's thought to be assumed.

For example:



	
  * firewall behavior

	
  * load balancer logic

	
  * request throttling

	
  * JVM configuration

	
  * appserver configuration

	
  * relationship of application to other apps in environment

	
  * how many applications are running within a JVM or on a box

	
  * thread pools and configuration (throttling, min/max, growth)

	
  * db pool config

	
  * database server config (memory, available connections to all applications, not just the one being deployed)

	
  * network latency and error thresholds

	
  * environment capacity

	
  * disclaimers on environmental issues which will affect application


[4] Since virtually nobody has an actual replica of production, dictate that an environment must be made available that everyone agrees on as being the 'spec' to which the app will be built and signed off on. The client must then accept that since their prod environment does not match that spec, any risk of issues going into prod are theirs -- such as bugs, crashes, delays, etc.

[5] If a client does not have adequate testing tools or refuses to provide opportunities for load testing (internal tools, Gomez, Keynote etc) then an official disclaimer must be communicated to the client (see above).

[6] Always get a baseline of a production environment before deployment:

	
  * thread dumps

	
  * application performance numbers

	
  * network errors/latency/performance

	
  * application logs


[7] Do not assume that because code has worked in other environments that it will work in your clients.

[8] The client doesn't care if it works anywhere else besides their prod environment -- even if it works in the dev environment they provided. See [4] above.
