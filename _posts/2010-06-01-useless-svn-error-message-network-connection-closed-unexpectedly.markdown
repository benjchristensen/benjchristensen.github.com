---
author: benjchristensen
comments: true
date: 2010-06-01 16:34:25+00:00
layout: post
slug: useless-svn-error-message-network-connection-closed-unexpectedly
title: 'Useless SVN Error Message: Network connection closed unexpectedly'
wordpress_id: 300
categories:
- Tools
---

If you're trying to do a subversion checkout using svn+ssh like this:

`
svn co svn+ssh://hostname/path
`

... and are getting a useless error like this ...

`svn: To better debug SSH connection problems, remove the -q option from 'ssh' in the [tunnels] section of your Subversion configuration file.
svn: Network connection closed unexpectedly`

Try removing .ssh/known_hosts (which fixed my issue) or ensure that the private/public keys in .ssh have the right permissions, such as this:

`benjchristensen-notebook:~ benjchristensen$ ls -al .ssh/
drwx------   6 benjchristensen  staff   204 Jun  1 09:30 .
drwxrwxrwx+ 39 benjchristensen  staff  1326 Jun  1 09:24 ..
-rw-------   1 benjchristensen  staff  1743 Jun  1 09:17 id_rsa
-rw-r--r--   1 benjchristensen  staff   423 Jun  1 09:17 id_rsa.pub
-rw-r--r--   1 benjchristensen  staff   413 Jun  1 09:30 known_hosts`


