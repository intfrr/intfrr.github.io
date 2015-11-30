---
layout: post
title: "Get ruby working in OSX 10.11 with rvm"
description: "Learning to get ruby working in OSX 10.11 with rvm for jekyll and zsh"
category: development
tagline: "Development lessons"
tags: [[tutorial]]
---
{% include JB/setup %}
This article describes how to get ruby working in OSX 10.11 with rvm for jekyll

# Overview

## What is RVM?

Ruby Version Manager, often abbreviated as RVM, is a unix-like software platform designed to manage multiple installations of Ruby on the same device.

## What is Jekyll

Jekyll is a simple, blog-aware, static site generator for personal, project, or organization sites. Written in Ruby by Tom Preston-Werner, GitHub's co-founder, it is distributed under an open source license.

## What is OSX 10.11 (El Capitan)

OS X El Capitan (el-kap-ɪ-tan) (version 10.11) is the twelfth major release of OS X, Apple Inc.'s desktop and server operating system for Macintosh computers. It is the successor to OS X Yosemite and focuses mainly on performance, stability and security.Following the California landmark-based naming scheme introduced with OS X Mavericks, El Capitan was named after a rock formation in Yosemite National Park.

The first beta of OS X El Capitan was released to developers shortly following the 2015 WWDC keynote on June 8, 2015. The first public beta was made available on July 9, 2015. There were multiple betas released after the keynote. OS X El Capitan was released to end users on September 30, 2015, as a free upgrade through the Mac App Store.

## What is Zsh

The Z shell (zsh) is a Unix shell that can be used as an interactive login shell and as a powerful command interpreter for shell scripting. Zsh can be thought of as an extended Bourne shell with a large number of improvements, including some features of bash, ksh, and tcsh.

### Examples

	$ rvm --default use 2.1.6
	Using /Users/dragon/.rvm/gems/ruby-2.1.6


	$ rjekyll serve
	Configuration file: /path-to-jekyll/_config.yml
	            Source: /path-to-jekyll/
	       Destination: /path-to-jekyll/_site
	      Generating...
	     Build Warning: Layout 'nil' requested in atom.xml does not exist.
	     Build Warning: Layout 'nil' requested in rss.xml does not exist.
	                    done.
	 Auto-regeneration: enabled for '/path-to-jekyll/'
	Configuration file: /path-to-jekyll/_config.yml
	    Server address: http://127.0.0.1:4000/
	  Server running... press ctrl-c to stop.


# How to make this happen

According to

	RVM is not a function, selecting rubies with 'rvm use ...' will not work.

	You need to change your terminal emulator preferences to allow login shell.
	Sometimes it is required to use `/bin/bash --login` as the command.
	Please visit https://rvm.io/integration/gnome-terminal/ for an example.

## Setup

On ```~/.zshrc```

	[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm" # Load RVM into     a shell session *as a function*

Reload zsh

	zsh

Then:

	sudo chown -R $(whoami):wheel /Library/Ruby/Gems
	sudo chown -R $(whoami):wheel /usr/local/bin
	sudo chown -R $(whoami):wheel /usr/local/share
	rvm get stable --auto-dotfiles

	rvm use 2.1.6


### Install
Then:

	rvm --default use 2.1.6

If you get something like:

	Ignoring RedCloth-4.2.9 because its extensions are not built.  Try: gem pristine RedCloth --version 4.2.9
	Ignoring bcrypt-3.1.10 because its extensions are not built.  Try: gem pristine bcrypt --version 3.1.10
	Ignoring fast-stemmer-1.0.2 because its extensions are not built.  Try: gem pristine fast-stemmer --version 1.0.2
	Ignoring ffi-1.9.8 because its extensions are not built.  Try: gem pristine ffi --version 1.9.8
	Ignoring gherkin-2.12.2 because its extensions are not built.  Try: gem pristine gherkin --version 2.12.2
	Ignoring json-1.8.3 because its extensions are not built.  Try: gem pristine json --version 1.8.3
	Ignoring msgpack-0.6.2 because its extensions are not built.  Try: gem pristine msgpack --version 0.6.2
	Ignoring network_interface-0.0.1 because its extensions are not built.  Try: gem pristine network_interface --version 0.0.1
	Ignoring nokogiri-1.6.6.2 because its extensions are not built.  Try: gem pristine nokogiri --version 1.6.6.2
	Ignoring pcaprub-0.12.0 because its extensions are not built.  Try: gem pristine pcaprub --version 0.12.0
	Ignoring pg-0.18.3 because its extensions are not built.  Try: gem pristine pg --version 0.18.3
	Ignoring pg_array_parser-0.0.9 because its extensions are not built.  Try: gem pristine pg_array_parser --version 0.0.9
	Ignoring posix-spawn-0.3.11 because its extensions are not built.  Try: gem pristine posix-spawn --version 0.3.11
	Ignoring rdiscount-2.1.7 because its extensions are not built.  Try: gem pristine rdiscount --version 2.1.7
	Ignoring redcarpet-3.3.2 because its extensions are not built.  Try: gem pristine redcarpet --version 3.3.2
	Ignoring redcarpet-3.2.3 because its extensions are not built.  Try: gem pristine redcarpet --version 3.2.3
	Ignoring sqlite3-1.3.10 because its extensions are not built.  Try: gem pristine sqlite3 --version 1.3.10
	Ignoring yajl-ruby-1.2.1 because its extensions are not built.  Try: gem pristine yajl-ruby --version 1.2.1
	Ignoring RedCloth-4.2.9 because its extensions are not built.  Try: gem pristine RedCloth --version 4.2.9
	Ignoring bcrypt-3.1.10 because its extensions are not built.  Try: gem pristine bcrypt --version 3.1.10
	Ignoring fast-stemmer-1.0.2 because its extensions are not built.  Try: gem pristine fast-stemmer --version 1.0.2
	Ignoring ffi-1.9.8 because its extensions are not built.  Try: gem pristine ffi --version 1.9.8
	Ignoring gherkin-2.12.2 because its extensions are not built.  Try: gem pristine gherkin --version 2.12.2
	Ignoring json-1.8.3 because its extensions are not built.  Try: gem pristine json --version 1.8.3
	Ignoring msgpack-0.6.2 because its extensions are not built.  Try: gem pristine msgpack --version 0.6.2
	Ignoring network_interface-0.0.1 because its extensions are not built.  Try: gem pristine network_interface --version 0.0.1
	Ignoring nokogiri-1.6.6.2 because its extensions are not built.  Try: gem pristine nokogiri --version 1.6.6.2
	Ignoring pcaprub-0.12.0 because its extensions are not built.  Try: gem pristine pcaprub --version 0.12.0
	Ignoring pg-0.18.3 because its extensions are not built.  Try: gem pristine pg --version 0.18.3
	Ignoring pg_array_parser-0.0.9 because its extensions are not built.  Try: gem pristine pg_array_parser --version 0.0.9
	Ignoring posix-spawn-0.3.11 because its extensions are not built.  Try: gem pristine posix-spawn --version 0.3.11
	Ignoring rdiscount-2.1.7 because its extensions are not built.  Try: gem pristine rdiscount --version 2.1.7
	Ignoring redcarpet-3.3.2 because its extensions are not built.  Try: gem pristine redcarpet --version 3.3.2
	Ignoring redcarpet-3.2.3 because its extensions are not built.  Try: gem pristine redcarpet --version 3.2.3
	Ignoring sqlite3-1.3.10 because its extensions are not built.  Try: gem pristine sqlite3 --version 1.3.10
	Ignoring yajl-ruby-1.2.1 because its extensions are not built.  Try: gem pristine yajl-ruby --version 1.2.1

Do:

	gem pristine RedCloth --version 4.2.9 &&  gem pristine bcrypt --version 3.1.10 &&  gem pristine fast-stemmer --version 1.0.2 &&  gem pristine ffi --version 1.9.8 &&  gem pristine gherkin --version 2.12.2 &&  gem pristine json --version 1.8.3 &&  gem pristine msgpack --version 0.6.2 &&  gem pristine network_interface --version 0.0.1 &&  gem pristine nokogiri --version 1.6.6.2 &&  gem pristine pcaprub --version 0.12.0 &&  gem pristine pg --version 0.18.3 &&  gem pristine pg_array_parser --version 0.0.9 &&  gem pristine posix-spawn --version 0.3.11 &&  gem pristine rdiscount --version 2.1.7 &&  gem pristine redcarpet --version 3.3.2 &&  gem pristine redcarpet --version 3.2.3 &&  gem pristine sqlite3 --version 1.3.10 &&  gem pristine yajl-ruby --version 1.2.1 &&  gem pristine RedCloth --version 4.2.9 &&  gem pristine bcrypt --version 3.1.10 &&  gem pristine fast-stemmer --version 1.0.2 &&  gem pristine ffi --version 1.9.8 &&  gem pristine gherkin --version 2.12.2 &&  gem pristine json --version 1.8.3 &&  gem pristine msgpack --version 0.6.2 &&  gem pristine network_interface --version 0.0.1 &&  gem pristine nokogiri --version 1.6.6.2 &&  gem pristine pcaprub --version 0.12.0 &&  gem pristine pg --version 0.18.3 &&  gem pristine pg_array_parser --version 0.0.9 &&  gem pristine posix-spawn --version 0.3.11 &&  gem pristine rdiscount --version 2.1.7 &&  gem pristine redcarpet --version 3.3.2 &&  gem pristine redcarpet --version 3.2.3 &&  gem pristine sqlite3 --version 1.3.10 &&  gem pristine yajl-ruby --version 1.2.1 &&


### Testing

Check jekyll:

	cd /path-to-jekyll/
	jekyll serve

You must get:

	Configuration file: /path-to-jekyll/_config.yml
	            Source: /path-to-jekyll/
	       Destination: /path-to-jekyll/_site
	      Generating...
	     Build Warning: Layout 'nil' requested in atom.xml does not exist.
	     Build Warning: Layout 'nil' requested in rss.xml does not exist.
	                    done.
	 Auto-regeneration: enabled for '/path-to-jekyll/'
	Configuration file: /path-to-jekyll/_config.yml
	    Server address: http://127.0.0.1:4000/
	  Server running... press ctrl-c to stop.


### Conclusion
Rvm is good if it s configured good

```DON'T FORGET TO USE TABS INSTEAD ON SPACES ON RB FILES``

### Authors:
Nadir Palacios
<a href="http://github.com/intfrr">http://github.com/intfrr</a>
