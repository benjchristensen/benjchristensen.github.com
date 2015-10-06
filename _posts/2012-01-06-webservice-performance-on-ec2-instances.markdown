---
author: benjchristensen
comments: true
date: 2012-01-06 03:24:50+00:00
layout: post
slug: webservice-performance-on-ec2-instances
title: WebService Performance on EC2 Instances
---

As part of a cost/performance analysis of [Amazon EC2 instances](http://aws.amazon.com/ec2/instance-types/) I wrote a [very simple Java webapp](https://github.com/benjchristensen/WSPerformanceTest) to allow simple comparison benchmarking.

The webapp runs in Tomcat and has a [servlet](https://github.com/benjchristensen/WSPerformanceTest/blob/master/src/com/wsperformancetest/ComputationalSimulationService.java) which returns a JSON response after looping to generate the JSON to cause CPU computation time as if the service were doing real work. It results in a lot of iteration and string creation activity – things web services do a lot of.

ApacheBenchmark (ab) was used as the test client to simulate traffic and capture statistics.

The instance types tested were [m2.2xlarge](https://github.com/benjchristensen/WSPerformanceTest/blob/master/testResults/2012_January5_EC2_Testing/machine_information_ec2_m2.2xlarge.txt), [m2.4xlarge](https://github.com/benjchristensen/WSPerformanceTest/blob/master/testResults/2012_January5_EC2_Testing/machine_information_ec2_m2.4xlarge.txt), [cc1.4xlarge](https://github.com/benjchristensen/WSPerformanceTest/blob/master/testResults/2012_January5_EC2_Testing/machine_information_ec2_cc1.4xlarge.txt), and [cc2.8xlarge](https://github.com/benjchristensen/WSPerformanceTest/blob/master/testResults/2012_January5_EC2_Testing/machine_information_ec2_cc2.8xlarge.txt).

The tests determined that the cc2.8xlarge instance type – though the most expensive by unit – is potentially the most cost effective type to use when serving large volume traffic involving a cluster of servers.

The cost to serve 1000 requests/second at a response time of approximately 18ms for each instance type is:



	
  * m2.2xlarge: $1.98

	
  * m2.4xlarge: $2.48

	
  * cc1.4xlarge: $1.36

	
  * **cc2.8xlarge: $1.19**


Of course, this test is very simplistic and ignores a wide variety of variables, but it demonstrates that the cc1 and cc2 boxes are well worth the time to evaluate for production application usage for achieving cost/performance efficiency.

The following graphs show the test results that were used to calculate the above costs.

**Results per Second with Increasing Concurrency**

This demonstrates how the 32 CPU cores on the cc2.8xlarge enable significantly higher throughput.

![](http://benjchristensen.files.wordpress.com/2012/01/requests_per_second_with_increasing_concurrency.png?w=800)

**Time per Request (ms) with Increasing Concurrency**

This shows how the response time degrades with increasing thread counts and how the larger boxes (particularly the cc2) scale better.

![](http://benjchristensen.files.wordpress.com/2012/01/time_per_request_with_increasing_concurrency.png?w=800)

**Spreadsheet**

This screenshot of the spreadsheet shows the cost calculations at each level of concurrency.

The hi-lighted green is considered the optimal "ceiling" beyond which performance degrades and throughput plateaus. This point is considered the high-water-mark that can be used to determine the number of machines in a cluster needed to serve a given amount of traffic and thus allow comparison of different machines.

![](http://benjchristensen.files.wordpress.com/2012/01/ec2-performance-data.png?w=800)

**Price per 1000 Requests per Second with Increasing Concurrency**

This scatter chart shows the cost to serve 1000 requests per second at increasing levels of concurrency on each instance type.

![](http://benjchristensen.files.wordpress.com/2012/01/price_with_increasing_concurrency.png?w=800)

Overall, the performance of the cc1 and cc2 boxes are impressive and their cost/performance appears to be far better than the m2 instances.

The raw results of the tests can be found on [Github](https://github.com/benjchristensen/WSPerformanceTest/tree/master/testResults/2012_January5_EC2_Testing).
