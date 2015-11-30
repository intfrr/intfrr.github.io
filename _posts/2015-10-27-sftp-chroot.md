---
layout: post
title: "SFTP Chroot"
description: "Learning to chroot users in sftp"
category: sysadmin
tagline: "Sysadmin lessons"
tags: [[tutorial]]
---
{% include JB/setup %}
This article describes how to chroot users in sftp

# Overview

## What is Sftp?

Secure ftp over ssh

### Examples

	sftp sftpuser@server.com

# How to make this happen

According to
<a href="https://wiki.archlinux.org/index.php/SFTP_chroot">https://wiki.archlinux.org/index.php/SFTP_chroot</a>

And then to
<a href="http://www.xpressfx.co.za/index.php/tutorials/linux/item/33-centos-7-setup-sftp-with-chroot-jail">http://www.xpressfx.co.za/index.php/tutorials/linux/item/33-centos-7-setup-sftp-with-chroot-jail</a>


## Setup

### Install
	groupadd sftpgroup
	useradd sftpuser -g sftpgroup -d /home/sftpgroup/sftpuser -s /bin/false
	passwd sftpuser
	mkdir /home/sftpgroup/sftpuser/www
	chown root /home/sftpgroup/sftpuser
	chmod 755 /home/sftpgroup/sftpuser
	chown sftpuser /home/sftpgroup/sftpuser/www
	chmod 755 /home/sftpgroup/sftpuser/www
	setsebool -P ssh_chroot_rw_homedirs on
	mkdir /home/sftpgroup/sftpuser/www/website
	chown -R sftpuser:apache /home/sftpgroup/sftpuser/www/website
	chmod g+s /home/sftpgroup/sftpuser/www/website
	chmod a-w /home/sftpgroup/sftpuser/*
	chmod a-w /home/sftpgroup/sftpuser/.*


### Testing

	sftp sftpuser@server.com
	sftpuser@server.com's password:
	Connected to server.com.
	sftp> cd www
	sftp> mkdir website
	sftp> ls
	website
	sftp> cd website
	sftp> mkdir test
	sftp> ls
	test

### Conclusion
	[root@xxxx home]# pwd
	/home
	[root@xxxx home]# ls -la
	total 4
	drwxr-xr-x.  5 root root   xx xxx xx xxxxxx .
	dr-xr-xr-x. 17 root root xxxx xxx xx xxxxxx ..
	drwxr-xr-x.  5 root root   xx xxx xx xxxxxx xxxxx
	drwxr-xr-x.  3 root root   xx xxx xx xxxxxx sftgroup
	drwxr-xr-x.  2 root root    x xxx xx xxxxxx xxxxxxxx
	[root@xxxx home]# cd sftgroup/
	[root@xxxx sftgroup]# pwd
	/home/sftgroup
	[root@xxxx sftgroup]# ls -la
	total 0
	drwxr-xr-x. 3 root root     xx xxx xx xxxxxx .
	drwxr-xr-x. 5 root root     xx xxx xx xxxxxx ..
	drwxr-xr-x. 4 root sftgroup xx xxx xx xxxxxx sftpuser
	[root@xxxx sftpgroup]# cd sftpuser/
	[root@xxxx sftpuser]# pwd
	/home/sftpgroup/sftpuser
	[root@xxxx sftpuser]# ls -al
	total 12
	dr-xr-xr-x. 4 root     sftgroup  xx xxx xx xxxxxx .
	dr-xr-xr-x. 3 root     root      xx xxx xx xxxxxx ..
	-r--r--r--. 1 sftpuser sftgroup  xx xxx x  xxxxxx .bash_logout
	-r--r--r--. 1 sftpuser sftgroup xxx xxx x  xxxxxx .bash_profile
	-r--r--r--. 1 sftpuser sftgroup xxx xxx x  xxxxxx .bashrc
	dr-xr-xr-x. 4 sftpuser sftgroup  xx xxx xx xxxxxx .mozilla
	dr-xr-xr-x. 3 sftpuser root      xx xxx xx xxxxxx www
	[root@xxxx sftpuser]# cd www
	[root@xxxx www]# pwd
	/home/sftgroup/sftpuser/www
	[root@xxxx www]# ls -la
	total 0
	dr-xr-xr-x. 3 sftpuser root     xx xxx xx xxxxxx .
	dr-xr-xr-x. 4 root     sftgroup xx xxx xx xxxxxx ..
	drwxr-xr-x. 2 sftpuser sftgroup  x xxx xx xxxxxx website
	[root@xxxx www]# cd website/
	[root@xxxx website]# pwd
	/home/sftgroup/sftpuser/www/website
	[root@xxxx website]# ls -la
	total 0
	drwxr-sr-x. 3 sftpuser apache xx xxx xx xxxxxx .
	dr-xr-xr-x. 3 sftpuser root   xx xxx xx xxxxxx ..
	drwxr-sr-x. 2 sftpuser apache  x xxx xx xxxxxx test
	[root@xxxx website]#

### Authors:
Unknown
<a href="http://www.xpressfx.co.za">http://www.xpressfx.co.za</a>

Nadir Palacios
<a href="http://github.com/intfrr">http://github.com/intfrr</a>



