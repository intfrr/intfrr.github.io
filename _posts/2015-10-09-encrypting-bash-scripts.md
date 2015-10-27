---
layout: post
title: "Encrypting bash scripts"
description: ""
category: lessons
tagline: "Sysadmin lessons"
tags: [[tutorial]]
---
{% include JB/setup %}
This article describes how to encrypt your bash scripts

# Overview

## What is Shc?

A generic shell script compiler. Shc takes a script, which is specified on the command line and produces C source code. The generated source code is then compiled and linked to produce a stripped binary executable.

The compiled binary will still be dependent on the shell specified in the first line of the shell code (i.e shebang) (i.e. #!/bin/sh), thus shc does not create com‐ pletely independent binaries.

shc itself is not a compiler such as cc, it rather encodes and encrypts a shell script and generates C source code with the added expiration capability. It then uses the system compiler to compile a stripped binary which behaves exactly like the original script. Upon execution, the compiled binary will decrypt and execute the code with the shell -c option.

### Examples

	shc -f test.bash -o test

# How to make this happen

According to
<a href="http://www.thegeekstuff.com/2012/05/encrypt-bash-shell-script/">http://www.thegeekstuff.com/2012/05/encrypt-bash-shell-script/</a>

And then to
<a href="http://neurobin.github.io/shc/">http://neurobin.github.io/shc/</a>


## Setup

### Install
	./configure
	make
	sudo make install


or simply run the binary file provided, in bin/x32 or bin/x64 in terminal

	./shc options


### For Ubuntu



	sudo add-apt-repository -y ppa:neurobin/ppa
	sudo apt-get update
	sudo apt-get install shc


### Testing

`cd to test "directory"...`

Output binary file will be test. If no output file is specified by the -o option, then it will create an executable with .x extension by default

### Known bugs
The one (and I hope the only) limitation using shc is the _SC_ARG_MAX system configuration parameter. It limits the maximum length of the arguments to the exec function, limiting the maximum length of the runnable script of shc. !! - CHECK YOUR RESULTS CAREFULLY BEFORE USING - !!

### Contribute:
If you are a developer, you can consider contributing to this project by forking this repository and making changes for better and do a pull request, or sharing ideas and suggestions or finding bugs, anything at all, what you think will be beneficial for this project.

If you aren't a developer, but still want to contribute, then you can support the contributing developers spiritually, by starring the repository and sharing ideas. If you want to be notified of the continuous development, you can add this in your watch list in Github.

If you see any problems or bugs please open an issue here

### Authors:
Francisco Rosales Garcia
<a href="frosal@fi.upm.es">frosal@fi.upm.es</a>

Jahidul Hamid
<a href="http://github.com/neurobin">http://github.com/neurobin</a>



