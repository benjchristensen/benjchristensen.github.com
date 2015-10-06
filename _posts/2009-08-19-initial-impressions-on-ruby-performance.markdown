---
author: benjchristensen
comments: true
date: 2009-08-19 04:09:37+00:00
layout: post
slug: initial-impressions-on-ruby-performance
title: Initial Impressions on Ruby Performance
---

I've spent the past day playing with Ruby and decided to test some basic performance - iterating and string parsing - to get an idea of what the performance is really like.

Ruby is not doing so well in my tests.

_Note to Ruby Experts: If anyone can demonstrate what I'm doing wrong in my code or testing, I would love to be corrected._

My approach was to write the exact same code in Java and Ruby that loads up a file, reads each lines, tokenizes it into words using whitespace as the delimiter and counts up the tokens.

This avoids network or database IO and other external resources - except the filesystem which I don't consider a significant variable in the test.

Further testing I'm planning on doing will test Rails, multi-threading and other common things I do in my apps.

[![Picture 3](http://benjchristensen.files.wordpress.com/2009/08/picture-31.png)](http://benjchristensen.files.wordpress.com/2009/08/picture-31.png)

On my laptop, a MacBook Pro 2.53Ghz Core 2 Duo with 4GB memory, the average times are:



	
  * Ruby 1.8.6 app: 8022ms

	
  * Java 5 app: 2986ms

	
  * Java 6 app: 1443ms


**Source Code**



	
  * [FileReadParse.java](http://benjchristensen.files.wordpress.com/2009/08/filereadparse-java.doc)

	
  * [file_read_parse.rb](http://benjchristensen.files.wordpress.com/2009/08/file_read_parse-rb.doc)


After downloading, strip the .doc ending off of the files.

**Program Output**


macbook-pro:src benjc$ /System/Library/Frameworks/JavaVM.framework/Versions/1.6/Home/bin/java FileReadParse




Starting to read file...




The number of tokens is: 7764115




It took 1502 ms




macbook-pro:performance benjc$ ruby file_read_parse.rb




Starting to read file ...




The number of tokens is: 7764115




It took 7999.955 ms


macbook-pro:src benjc$ /System/Library/Frameworks/JavaVM.framework/Versions/1.6/Home/bin/java FileReadParse

Starting to read file...

The number of tokens is: 7764115

It took 1502 ms

macbook-pro:performance benjc$ ruby file_read_parse.rb

Starting to read file ...

The number of tokens is: 7764115

It took 7999.955 ms



