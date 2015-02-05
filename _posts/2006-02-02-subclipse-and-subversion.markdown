---
author: benjchristensen
comments: true
date: 2006-02-02 19:26:00+00:00
layout: post
slug: subclipse-and-subversion
title: Subclipse and Subversion
wordpress_id: 8
categories:
- Tools
---

Subclipse is a pretty decent plugin for Subversion ... though it feels like it still has some maturing to do ...

Here are two items in particular we've run into ...

1) Folder named "tags" doesn't think it's under version control

If a folder is named "tags" anywhere ... and it says it's ignored, or won't synchronize etc, then go into Preferences for Team -> Ignored Resources and uncheck "tags"

2) Rename of Class name or other file fails with an SVN error

On Windows ... if all you're doing is changing the CASE of a filename ... it will fail since Windows is case-insensitive.

So ... you need to change the name to something different first .... then to the renamed file with different case.

Example:

- ClassName
- ClassNameOld
- CLASSName

Ben
