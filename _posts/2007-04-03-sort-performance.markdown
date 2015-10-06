---
author: benjchristensen
comments: true
date: 2007-04-03 14:30:01+00:00
layout: post
slug: sort-performance
title: Sort Performance
---

We did some simple testing on various sort algorithms we found and compared them with the Java Arrays.sort QuickSort implementation.

This is rudimentary testing since it's not attempting to test all the variety of distributions of numbers that could exist and should be tested.

That being said, we are creating a collection of 50k, 500k, or 5million numbers randomly generated, and then cloning that collection to be sorted by each of the algorithms.

This first test had 1/2 the numbers as 4 digits, the other half as 5 digits meaning that in the larger collects, there should be a lot of duplicates.

The second test below had 1/2 the numbers as 4 digits, the other half as 8 digits.

This change in number of digits makes dramatic changes for FlashSort and completely breaks it.

Radix is just bad all the time ... I have yet to figure out where it's strength lies.

This is not thorough enough to make any conclusion, but I found it interesting nonetheless.

***Test 1 with 4 & 5 digit numbers***

-----------------------------
Run with 50k
-----------------------------
Arrays.sort(int) => 15ms
FlashSort.sort(int) => 11ms  Valid: true
fastqs.sort(int) => 10ms  Valid: true
eqsort.sort(int) => 16ms  Valid: true
radix.sort(int) => 175ms  Valid: true
radix.sort(int, 5) => 130ms  Valid: true
-----------------------------
Run with 500k
-----------------------------
Arrays.sort(int) => 101ms
FlashSort.sort(int) => 56ms  Valid: true
fastqs.sort(int) => 72ms  Valid: true
eqsort.sort(int) => 96ms  Valid: true
radix.sort(int) => 2164ms  Valid: true
radix.sort(int, 5) => 1203ms  Valid: true
-----------------------------
Run with 5million
-----------------------------
Arrays.sort(int) => 748ms
FlashSort.sort(int) => 717ms  Valid: true
fastqs.sort(int) => 780ms  Valid: true
eqsort.sort(int) => 1625ms  Valid: true
radix.sort(int) => 82218ms  Valid: true
radix.sort(int, 5) => 11387ms  Valid: true
-----------------------------

***Test 1 with 4 & 8 digit numbers***

-----------------------------
Run with 50k
-----------------------------
Arrays.sort(int) => 14ms
FlashSort.sort(int) => 662ms  Valid: true
fastqs.sort(int) => 10ms  Valid: true
eqsort.sort(int) => 11ms  Valid: true
radix.sort(int) => 294ms  Valid: true
radix.sort(int, 8 ) => 225ms  Valid: true
-----------------------------
Run with 500k
-----------------------------
Arrays.sort(int) => 91ms
FlashSort.sort(int) => 17832ms  Valid: true
fastqs.sort(int) => 72ms  Valid: true
eqsort.sort(int) => 95ms  Valid: true
radix.sort(int) => 2066ms  Valid: true
radix.sort(int, 8 ) => 2003ms  Valid: true
-----------------------------
Run with 5million
-----------------------------
Arrays.sort(int) => 909ms
FlashSort.sort(int) => 197796ms  Valid: true
fastqs.sort(int) => 825ms  Valid: true
eqsort.sort(int) => 1494ms  Valid: true
radix.sort(int) => 22957ms  Valid: true
radix.sort(int, 8 ) => 20041ms  Valid: true
-----------------------------
