---
author: benjchristensen
comments: true
date: 2006-09-02 00:46:00+00:00
layout: post
slug: add-all-new-files-with-svn
title: Add All New Files with SVN
wordpress_id: 16
categories:
- Code
---

Add this to .bash_profile for a quick command line for adding all new files in a working directory.

svn_add_all(){
svn status | grep "^?" | awk '{print $2}' | xargs svn add
}
