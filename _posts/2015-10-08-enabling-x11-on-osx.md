---
layout: post
title: "Enabling X11 on OSX"
description: ""
category: lessons
tagline: "Sysadmin lessons"
tags: [[tutorial]]
---
{% include JB/setup %}
This article describes how to enable X11 in OSX to launch XQuartz automatically

# Overview

## What is XQuartz?

XQuartz (formerly and often still informally referred to as X11.app) is Apple Inc.'s version of the X server, a component of the X Window System, for Mac OS X. The X Window System is a standard framework for creating applications with a graphical user interface on Unix-like operating systems. XQuartz is therefore required to allow cross-platform applications not specifically designed for OS X to run on it, including much scientific and academic software. The name derives from Quartz, the OS X graphics framework, to which XQuartz connects these applications.

### Examples

ssh -X user@remote

And automatically the app loads up.


# How to make this happen

According to
`http://apple.stackexchange.com/questions/91250/start-xquartz-automatically-on-x11-app-launch`

And then to
`http://xquartz.macosforge.org/trac/wiki/X11-UsersFAQ#sshXforwardingdebugging`

This was the solution


## Setup

### ssh X forwarding debugging

Mountain Lion Users, please note that there is a known issue sshing into a ML server. To get X11 forwarding working, please add the following to /etc/sshd_config:

XauthLocation /opt/X11/bin/xauth
Try these SSH troubleshooting steps. This list shows the expected behavior of the system.

local $ — refers to commands run on your local Mac running Leopard

remote $ — refers to commands run on a remote Unix machine, of any type

[1] local $ echo $DISPLAY
/tmp/launch-Bh0fLm/:0
[2] local $ grep DISPLAY ~/.*rc ~/.login ~/.*profile ~/.MacOSX/environment.plist 2>/dev/null
[3] local $ grep -r DISPLAY /opt/local/etc /sw/etc /etc 2>/dev/null
[4] local $ ssh -Y remote
Warning: No xauth data; using fake authentication data for X11 forwarding.
[5] remote $ echo $DISPLAY
localhost:10.0
[6] remote $ grep X11 /etc/ssh/sshd_config ~/.ssh/*
X11Forwarding yes
X11DisplayOffset 10
Notes:

If step 1 returns :0, localhost:0 or anything similar, you have a configuration file that is overriding launchd's $DISPLAY.

If step 2 outputs anything, it indicates that a configuration file in your home directory may be the culprit; try creating a new user and repeating the steps with that user.

If step 3 outputs anything, it indicates that a system-wide change was made that is overriding your environment. If it begins with /opt/local, it is MacPorts; if it begins with /sw, it is Fink. Otherwise, it is probably a commercial program that uses X11; contact your vendor for an updated version.

The warning message in step 4 is harmless.

If step 5 does not output anything, then step 6's results probably include X11Forwarding no. In this case, you must fix the configuration on the remote side.

If step 5 outputs anything other than localhost:xx.0, then your remote configuration is overriding the DISPLAY environment variable set by sshd on the remote side.

## Further setup

### Suppressing xterm launching by default.

In Leopard, xterm is run directly by X11.app which causes the server to start. Think of X11.app as something that *just* executes xterm. If you want to change this from xterm to something else, you can change the application run by doiing the following:

(XQuartz.app) defaults write org.macosforge.xquartz.X11 app_to_run <whatever you want to run>
(Apple's X11.app) defaults write org.x.X11 app_to_run <whatever you want to run>
(MacPorts' X11.app) defaults write org.macports.X11 app_to_run <whatever you want to run>
So if you want nothing to run, you can accomplish this by:

defaults write org.macosforge.xquartz.X11 app_to_run /usr/bin/true
If you launch XQuartz.app from the dock or run "open -a XQuartz" it will run app_to_run.

Note: For versions prior to the X11-2.1.1 package, use the following instead:

defaults write org.x.X11_launcher app_to_run /usr/X11/bin/xdpyinfo

## Conclusion

Don't mess up with environment variables.

**Thank you** for reading this far.

## Next Steps

Learn how to debug xauth.
http://superuser.com/questions/805725/how-do-i-debug-x11-connection-rejected-because-of-wrong-authentication
