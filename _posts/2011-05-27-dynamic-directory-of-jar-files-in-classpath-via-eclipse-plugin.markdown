---
author: benjchristensen
comments: true
date: 2011-05-27 04:34:24+00:00
layout: post
slug: dynamic-directory-of-jar-files-in-classpath-via-eclipse-plugin
title: Dynamic Directory of Jar Files in Classpath via Eclipse Plugin
---

I came across a scenario where I needed Eclipse to dynamically add a folder of jar files to the classpath and found out that Eclipse doesn't support this out of the box (no idea why ... IntelliJ does).

So I began Googling and found "how" to solve it by writing a classpath container but could find a pre-packaged solution.

The how was explained here: [https://www.ibm.com/developerworks/opensource/tutorials/os-eclipse-classpath/](https://www.ibm.com/developerworks/opensource/tutorials/os-eclipse-classpath/)

I took that example and tweaked it into a working plugin. It now lives at [GitHub](https://github.com/benjchristensen/SimpleDirectoryContainer_EclipsePlugin) where the plugin and source can be downloaded.

Once the plugin is installed in Eclipse, edit the "Java Build Path" on a project and click "Add Library" and choose "Directory Container":

[![](http://benjchristensen.files.wordpress.com/2011/05/add-library.png?w=800)](http://benjchristensen.files.wordpress.com/2011/05/add-library.png)

Then choose the folder (a subfolder of the project so it's relative) and defines what file extensions it should include:

[![](http://benjchristensen.files.wordpress.com/2011/05/creating-library.png?w=800)](http://benjchristensen.files.wordpress.com/2011/05/creating-library.png)

Once saved this library will show up like any other Eclipse classpath library and show all Jar files from the selected folder ... and most importantly will dynamically update the classpath when refreshed to whatever is in that folder.
[![](http://benjchristensen.files.wordpress.com/2011/05/directory-classpath.png?w=800)](http://benjchristensen.files.wordpress.com/2011/05/directory-classpath.png)

I hope this helps someone else needing the same behavior in Eclipse!

