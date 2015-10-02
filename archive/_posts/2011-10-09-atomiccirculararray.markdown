---
author: benjchristensen
comments: true
date: 2011-10-09 05:42:41+00:00
layout: post
slug: atomiccirculararray
title: AtomicCircularArray Wins My Concurrency Throughput Test
wordpress_id: 399
categories:
- Code
- Performance
---

I recently made several implementations of a RollingNumber (allowing a sum to be calculated over a 10 second period with 1 second increments with continual updates) to determine what would perform best under high-concurrency.

In my case, concurrency means 4-8000 writes/second from hundreds of threads on an 8-core machine and only a handful of reads per second.

In the end, a circular-array (using AtomicReferenceArray internally) won my throughput tests and also achieved my side goal of being non-blocking.

The [code is on GitHub](https://github.com/benjchristensen/RollingNumberConcurrencyTesting) and the winning implementation is [RollingNumberViaTryLockWithAtomicCircularArray](https://github.com/benjchristensen/RollingNumberConcurrencyTesting/blob/master/src/RollingNumberViaTryLockWithAtomicCircularArray.java).

Note that this code is NOT what I would deploy in production, since I forced each implementation to comply to the same interface so they could all be run by my test-harness.

However, a modified version of RollingNumberViaTryLockWithAtomicCircularArray is being run in production processing billions of writes per day.

Another aspect of the test is the use of ReentrantLock.tryLock() instead of a synchronized block. The tryLock() works well in this use-case, allowing only 1 thread to get the lock and routing all others around it instead of blocking them.

**Test Results**

Here are charts (higher is better) showing the differences in performance between implementations on two different machines:

**MacBook Pro 2.2GHz Intel Core i7, 8GB Memory, SSD Drive, OSX Lion 10.7.1**

    
    $ uname -a
    Darwin 11.1.0 Darwin Kernel Version 11.1.0: Tue Jul 26 16:07:11 PDT 2011; root:xnu-1699.22.81~1/RELEASE_X86_64 x86_64
    
    $ java -version
    java version "1.6.0_26"
    Java(TM) SE Runtime Environment (build 1.6.0_26-b03-383-11A511)
    Java HotSpot(TM) 64-Bit Server VM (build 20.1-b02-383, mixed mode)



The winner is the blue bar which is the highest.

[![](http://benjchristensen.files.wordpress.com/2011/10/concurrent_throughput_rollingnumber_macbookpro.png?w=800)](http://benjchristensen.files.wordpress.com/2011/10/concurrent_throughput_rollingnumber_macbookpro.png)

**Amazon EC2 m2.4xlarge**
High-Memory Quadruple Extra Large Instance 68.4 GB of memory, 26 EC2 Compute Units (8 virtual cores with 3.25 EC2 Compute Units each), 1690 GB of local instance storage, 64-bit platform

    
    $ uname -a
    Linux 2.6.21.7-2.ec2.v1.3.fc8xen #1 SMP Sat Sep 25 01:16:50 EDT 2010 x86_64 x86_64 x86_64 GNU/Linux
    
    $ /usr/java/latest/bin/java -version
    java version "1.6.0_25"
    Java(TM) SE Runtime Environment (build 1.6.0_25-b06)
    Java HotSpot(TM) 64-Bit Server VM (build 20.0-b11, mixed mode)



The winner is the orange bar which is the highest.

[![](http://benjchristensen.files.wordpress.com/2011/10/concurrent_throughput_rollingnumber_ec2.png?w=800)](http://benjchristensen.files.wordpress.com/2011/10/concurrent_throughput_rollingnumber_ec2.png)

**Running the Test**

You can run the test using an [executable JAR](https://github.com/downloads/benjchristensen/RollingNumberConcurrencyTesting/RollingNumberThroughputTest.jar) with the command:


    
    
    java -Xmx1g -jar RollingNumberThroughputTest.jar
    



The test also validates that the code does what it should and is able to find non-thread-safe implementations by looking for incorrect math caused by concurrency bugs.

**Conclusion**

I found it very interesting how differently the results were on the 2 machines (operating systems and CPUs are very different, the JVM implementations are also different). In both cases though the AtomicCircularArray performed better, far better on the EC2 instance running the Sun JVM.

These tests provided me with the data to choose AtomicCircularArray and as mentioned above it is similar to what I'm now using in production.
