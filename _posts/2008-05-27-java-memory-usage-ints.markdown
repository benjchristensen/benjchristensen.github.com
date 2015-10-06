---
author: benjchristensen
comments: true
date: 2008-05-27 07:41:01+00:00
layout: post
slug: java-memory-usage-ints
title: Java Memory Usage - Ints
---

As I work on another set of indexes with large numbers of ints I've revisited how different storage mechanisms behave.

I've set the JVM to just over 64MB (70MB to be precise).

An int being 4 bytes means that 64MB of ints is as follows:

       int sixtyFourMB = 64 * 1024 * 1024 / 4;

That is 16,777,216 ints.

An int array can successfully store 64MB in the JVM meaning it is properly assigning each int to 4 bytes without overhead.

      int[] vals = new int[sixtyFourMB];

However, if you use ArrayList<Integer> you run out of memory after 3,392,918 ints being added.

That is 1/5 of what can be stored in the int[]!

Now, assigning the space to ArrayList is fine:

                ArrayList<Integer> ints = new ArrayList<Integer>(sixtyFourMB);

It's when you add the Integer objects (int is cast to Integer behind the scenes in JDK 5) that it dies 1/5 in.

So the overhead is obviously in the Integer object.

I next try the Trove library and use the TIntArrayList.

If I leave it to assign its memory space by default, it runs out of memory at 10,485,760 (62%).

If however I tell it how many ints to expect it sizes itself properly and does not try to grow too large and fits the entire 64MB.

     TIntArrayList ints = new TIntArrayList(sixtyFourMB);

Thus, when backed by an int[] the memory can be efficiently stored, but when using an Object[] memory is very inefficient when attempting to store primitive ints.

Out of curiosity for what an Object() really does with memory I did the following:

            ArrayList<Object> ints = new ArrayList<Object>(sixtyFourMB);

            for (i = 0; i < sixtyFourMB; i++) {

                ints.add(null);

            }

That works, it all fits in memory.

If however I change the "null" to "new Object()" such as:

                ints.add(new Object());

It fails at 702065 ... which means that the object[] has already taken up the space and there is no room for the objects on the heap.

Thus, for storage of simple data primitive arrays is MUCH more efficient.

If the flexibility of the Collections API is needed for dynamic manipulation of those arrays then use [GNU Trove](http://trove4j.sourceforge.net/) ... but carefully or the dynamic sizing of the arrays in the background can cause a lot of waste.

 

An old but interesting article specifies memory usage by normal objects and classes:

http://www.roseindia.net/javatutorials/determining_memory_usage_in_java.shtml

Here are two points from that article of note:



	
  1. The class takes up at least 8 bytes. So, if you say `**new** Object();` you will allocate 8 bytes on the heap.

	
  2. Each data member takes up 4 bytes, except for long and double which take up 8 bytes. Even if the data member is a byte, it will still take up 4 bytes! In addition, the amount of memory used is increased in 8 byte blocks. So, if you have a class that contains one byte it will take up 8 bytes for the class and 8 bytes for the data, totalling 16 bytes (groan!).



