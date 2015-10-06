---
author: benjchristensen
comments: true
date: 2006-03-31 22:25:00+00:00
layout: post
slug: jboss-and-session-persistence
title: JBoss and session persistence
---

JBoss 4.0.3 by default has session persistence turned off.

[JBoss WIKI](http://wiki.jboss.org/wiki/Wiki.jsp?page=DisableSessionPersistence)

the context.xml file:

# pwd
/apps/jboss/server/default/deploy/jbossweb-tomcat55.sar
# more context.xml





org.jboss.web.tomcat.security.RunAsListener
