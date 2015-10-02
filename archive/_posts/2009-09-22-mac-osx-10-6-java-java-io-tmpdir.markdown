---
author: benjchristensen
comments: true
date: 2009-09-22 20:50:15+00:00
layout: post
slug: mac-osx-10-6-java-java-io-tmpdir
title: Mac OSX 10.6 Java - java.io.tmpdir
wordpress_id: 277
categories:
- Code
---

Migrating from OSX 10.5 to Snow Leopard, 10.6 caused all of my java projects using embedded MySQL MXJ to fail.

I found that this was because Java returns a very odd path for the "java.io.tmpdir" property:

_/private/var/folders/b4/b44x97M0GFydt3jCKcowsU+++TI/-Tmp-/_

This causes issues with MySQL MXJ as it converts the + signs into spaces so the path becomes:

_/private/var/folders/b4/b44x97M0GFydt3jCKcowsU TI/-Tmp-/_

The original code was:

private static File tmpDir = new File(System.getProperty("java.io.tmpdir"));

To fix it I put in the following hack so that MySQL MXJ will now work again and I can still use the "java.io.tmpdir" property on other systems such as Windows:

private static File ourAppDir;

static {
String tempPath = System.getProperty("java.io.tmpdir");
// a fix to handle the crazy path the Mac JVM returns
if (tempPath.startsWith("/var/folders/")) tempPath = "/tmp/";
ourAppDir = new File(tempPath);
}
