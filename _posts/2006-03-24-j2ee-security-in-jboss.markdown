---
author: benjchristensen
comments: true
date: 2006-03-24 23:10:00+00:00
layout: post
slug: j2ee-security-in-jboss
title: J2EE Security in JBoss
---

In the login-config.xml file

<application-policy name = "VTNSite">
<authentication>

<login-module code="org.jboss.security.auth.spi.UsersRolesLoginModule" flag = "required">

<module-option name="usersProperties">props/console-users.properties</module-option>

<module-option name="rolesProperties">props/console-roles.properties</module-option>

</login-module>

</authentication>
</application-policy>

/server/default/conf/props> more console-roles.properties 
# A sample roles.properties file for use with the UsersRolesLoginModule
admin=VTNSysAdmin

/server/default/conf/props> more console-users.properties 
# A sample users.properties file for use with the UsersRolesLoginModule
admin=mypassword
