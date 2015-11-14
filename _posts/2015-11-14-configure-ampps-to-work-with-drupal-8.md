---
layout: post
title: "Configure AMPPS to work with Drupal 8"
description: "Learn to configure AMPPS to work with Drupal 8"
category: lessons
tagline: "Sysadmin lessons"
tags: [[tutorial]]
---
{% include JB/setup %}
This article describes how to configure AMPPS to work with Drupal 8

# Overview

## What is Drupal 8?

Drupal 8 is the latest, greatest release of the world's most widely used enterprise web CMS. It's fast. Flexible. Drupal 8 taps into the concentrated innovation from its open source community.

## What is AMPPS?

AMPPS is a solution stack of Apache, MySQL, MongoDB, PHP, Perl & Python for Windows, Linux and Mac. It comes with over 300 PHP web applications, over 1000 PHP classes and various versions of PHP. AMPPS is created by Softaculous Ltd. a company founded in 2009 which makes the Softaculous Auto installer. AMPPS is available on Windows and Macintosh systems and is used to develop on PHP, MySQL applications like WordPress, Joomla, Drupal, etc.

### Examples

<a href="https://www.drupal.org/files/People__Drupal_8_is_here!_-_Google_Chrome_2013-02-18_02-04-28.png">https://www.drupal.org/files/People__Drupal_8_is_here!_-_Google_Chrome_2013-02-18_02-04-28.png</a>

<a href="http://i1-mac.softpedia-static.com/screenshots/AMPPS_1.jpg">http://i1-mac.softpedia-static.com/screenshots/AMPPS_1.jpg</a>


# How to make this happen

According to
<a href="http://stackoverflow.com/questions/21073747/fatal-error-call-to-undefined-function-mb-strtolower">http://stackoverflow.com/questions/21073747/fatal-error-call-to-undefined-function-mb-strtolower</a>

And
<a href="http://stackoverflow.com/questions/8037245/zend-framework-call-to-undefined-function-token-get-all
">http://stackoverflow.com/questions/8037245/zend-framework-call-to-undefined-function-token-get-all
</a>

And then to
<a href="http://stackoverflow.com/questions/21114371/php-curl-error-code-60">http://stackoverflow.com/questions/21114371/php-curl-error-code-60</a>


## Setup

### Install
	php -i | grep ini
	vim /path-to-php/php.ini
	zend.multibyte = On
	extension=mbstring.so
	--Note: Use curl.haxx.se/ca/cacert.pem
	curl.cainfo = "path_to_cert/cacert.pem"
	extension=tokenizer.so



### Testing

	http://path-to-drupal/

### Conclusion
	AMPPS overrides php.ini everytime you change a configuration from GUI tool

### Authors:
Nadir Palacios
<a href="http://github.com/intfrr">http://github.com/intfrr</a>
