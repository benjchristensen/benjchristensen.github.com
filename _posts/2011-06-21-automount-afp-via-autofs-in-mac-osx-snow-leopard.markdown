---
author: benjchristensen
comments: true
date: 2011-06-21 20:51:34+00:00
layout: post
slug: automount-afp-via-autofs-in-mac-osx-snow-leopard
title: Automount AFP via autofs in Mac OSX (Snow Leopard)
---

I wanted a mount point that was automatic from my desktop to laptop and didn't need me to manually re-connect each time I came back to it.

After a bit of research, trial and error I figured out the correct incantation:

Edit the /etc/fstab (create if not there) to be:
`
HOSTNAME:MOUNTPOINT /PATH_ON_MACHINE_TO_USE_AS_MOUNT url automounted,url==afp://USERNAME:PASSWORD@HOSTNAME/MOUNTPOINT 0 0
`

Note that "MOUNTPOINT" on Mac for a users directory is NOT "/Users/username", it is just "username".

To restart the automounter type:
`
automount -vc
`

It will mount the newly defined mountpoint and create the folder defined with PATH_ON_MACHINE_TO_USE_AS_MOUNT.


Some links I found useful while researching:

[http://forums.plexapp.com/index.php/topic/14201-howto-automount-afpsmb-shares-using-autofs/](http://forums.plexapp.com/index.php/topic/14201-howto-automount-afpsmb-shares-using-autofs/)
[http://rajeev.name/2007/11/23/autofs-goodness-in-apples-leopard-105-part-ii/](http://rajeev.name/2007/11/23/autofs-goodness-in-apples-leopard-105-part-ii/)
