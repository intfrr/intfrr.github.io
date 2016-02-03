---
layout: post
title: "Ionic setup on OSX 10.11 with android and ios emulators and zsh"
description: "Learning to setup on OSX 10.11 with android and ios emulators and zsh"
category: development
tagline: "Development lessons"
tags: [[tutorial]]
---
{% include JB/setup %}
This article describes how to get ionic up and running on osx and android and ios emulators

# Overview

## What is Ionic?

Ionic is a complete open-source SDK for hybrid mobile app development. Built on top of AngularJS and Apache Cordova, Ionic provides tools and services for developing hybrid mobile apps using Web technologies like CSS, HTML5, and Sass. Apps can be built with these Web technologies and then distributed through native app stores to be installed on devices by leveraging Cordova. Ionic was created by Max Lynch, Ben Sperry, and Adam Bradley of Drifty Co. in 2013, and is used by software developers around the World.

## What is Android

Android is a mobile operating system (OS) currently developed by Google, based on the Linux kernel and designed primarily for touchscreen mobile devices such as smartphones and tablets. Android's user interface is mainly based on direct manipulation, using touch gestures that loosely correspond to real-world actions, such as swiping, tapping and pinching, to manipulate on-screen objects, along with a virtual keyboard for text input. In addition to touchscreen devices, Google has further developed Android TV for televisions, Android Auto for cars, and Android Wear for wrist watches, each with a specialized user interface. Variants of Android are also used on notebooks, game consoles, digital cameras, and other electronics. As of 2015, Android has the largest installed base of all operating systems. It is the second most commonly used mobile operating system in the United States, while iOS is the first.

Initially developed by Android, Inc., which Google bought in 2005, Android was unveiled in 2007, along with the founding of the Open Handset Alliance – a consortium of hardware, software, and telecommunication companies devoted to advancing open standards for mobile devices. As of July 2013, the Google Play store has had over one million Android applications ("apps") published, and over 50 billion applications downloaded. An April–May 2013 survey of mobile application developers found that 71% of developers create applications for Android, and a 2015 survey found that 40% of full-time professional developers see Android as their priority target platform, which is comparable to Apple's iOS on 37% with both platforms far above others. At Google I/O 2014, the company revealed that there were over one billion active monthly Android users, up from 538 million in June 2013.

Android's source code is released by Google under open source licenses, although most Android devices ultimately ship with a combination of open source and proprietary software, including proprietary software required for accessing Google services. Android is popular with technology companies that require a ready-made, low-cost and customizable operating system for high-tech devices. Its open nature has encouraged a large community of developers and enthusiasts to use the open-source code as a foundation for community-driven projects, which add new features for advanced users or bring Android to devices originally shipped with other operating systems. At the same time, as Android has no centralised update system most Android devices fail to receive security updates: research in 2015 concluded that almost 90% of Android phones in use had known but unpatched security vulnerabilities due to lack of updates and support. The success of Android has made it a target for patent litigation as part of the so-called "smartphone wars" between technology companies.

## What is iOS

iOS (originally iPhone OS) is a mobile operating system created and developed by Apple Inc. and distributed exclusively for Apple hardware. It is the operating system that presently powers many of the company's mobile devices, including the iPhone, iPad, and iPod touch. In October 2015, it was the most commonly used mobile operating system, in a few countries, such as in Canada, the United States, the United Kingdom, Norway, Sweden, Denmark, Japan, and Australia, while iOS is far behind Google's Android globally; iOS had a 19.7% share of the smartphone mobile operating system units shipped in the fourth quarter of 2014, behind Android with 76.6%. However, on tablets, iOS the most commonly used tablet operating system in the world.

Originally unveiled in 2007, for the iPhone, it has been extended to support other Apple devices such as the iPod Touch (September 2007), iPad (January 2010), iPad Mini (November 2012) and second-generation Apple TV onward (September 2010). As of January 2015, Apple's App Store contained more than 1.4 million iOS applications, 725,000 of which are native for iPads. These mobile apps have collectively been downloaded more than 100 billion times.

The iOS user interface is based on the concept of direct manipulation, using multi-touch gestures. Interface control elements consist of sliders, switches, and buttons. Interaction with the OS includes gestures such as swipe, tap, pinch, and reverse pinch, all of which have specific definitions within the context of the iOS operating system and its multi-touch interface. Internal accelerometers are used by some applications to respond to shaking the device (one common result is the undo command) or rotating it in three dimensions (one common result is switching from portrait to landscape mode).

iOS shares with OS X some frameworks such as Core Foundation and Foundation Kit; however, its UI toolkit is Cocoa Touch rather than OS X's Cocoa, so that it provides the UIKit framework rather than the AppKit framework. It is therefore not compatible with OS X for applications. Also while iOS also shares the Darwin foundation with OS X, Unix-like shell access is not available for users and restricted for apps, making iOS not fully Unix-compatible either.

Major versions of iOS are released annually. The current release, iOS 9.1, was released on October 21, 2015. In iOS, there are four abstraction layers: the Core OS layer, the Core Services layer, the Media layer, and the Cocoa Touch layer. The current version of the operating system (iOS 9), dedicates around 1.3 GB of the device's flash memory for iOS itself. It runs on the iPhone 4S and later, iPad 2 and later, iPad Pro, all models of the iPad Mini, and the 5th-generation iPod Touch and later.

## What is OSX 10.11 (El Capitan)

OS X El Capitan (el-kap-ɪ-tan) (version 10.11) is the twelfth major release of OS X, Apple Inc.'s desktop and server operating system for Macintosh computers. It is the successor to OS X Yosemite and focuses mainly on performance, stability and security.Following the California landmark-based naming scheme introduced with OS X Mavericks, El Capitan was named after a rock formation in Yosemite National Park.

The first beta of OS X El Capitan was released to developers shortly following the 2015 WWDC keynote on June 8, 2015. The first public beta was made available on July 9, 2015. There were multiple betas released after the keynote. OS X El Capitan was released to end users on September 30, 2015, as a free upgrade through the Mac App Store.

## What is an emulator

In computing, an emulator is hardware or software that enables one computer system (called the host) to behave like another computer system (called the guest). An emulator typically enables the host system to run software or use peripheral devices designed for the guest system.

## What is Zsh

The Z shell (zsh) is a Unix shell that can be used as an interactive login shell and as a powerful command interpreter for shell scripting. Zsh can be thought of as an extended Bourne shell with a large number of improvements, including some features of bash, ksh, and tcsh.

### Examples

	$ cd MyApp
	$ ionic emulate android
	  ...(Output ommited)

	  BUILD SUCCESSFUL

	  Total time: 2.644 secs
	  Built the following apk(s):
	      /Users/Desktop/MyApp/platforms/android/build/outputs/apk/android-debug.apk
	  Installing app on emulator...
	  Using apk:/Users/Desktop/MyApp/platforms/android/build/outputs/apk/android-debug.apk
	  INSTALL SUCCESS
	  Unlocking screen...
	  Launching application...
	  LAUNCH SUCCESS

	$ ionic emulate ios
	  ...(Output ommited)

	  ** BUILD SUCCEEDED **

	  No target specified for emulator. Deploying to iPhone-6 simulator
	  com.ionicframework.starter: 73300
	  ** RUN SUCCEEDED **


# How to make this happen

According to

<a href="http://digitaldrummerj.me/ionic-setup-osx/">http://digitaldrummerj.me/ionic-setup-osx/</a>

And

<a href="http://dara.azurewebsites.net/ionic-android-osx/">http://dara.azurewebsites.net/ionic-android-osx/</a>

And

<a href="http://ionicframework.com/docs/guide/testing.html">http://ionicframework.com/docs/guide/testing.html</a>

And then to

	******************************************************
	 Dependency warning - for the CLI to run correctly,
	 it is highly suggested to install/upgrade the following:

	 Please install your Cordova CLI to version  >=4.2.0 `npm install -g cordova`

	******************************************************
	1.7.10


## Setup

1. Android setup
	1. JDK

		Download from

		<a href="http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html">http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html</a>

		After install on the terminal

			$ vim ~/.zshrc

				export JAVA_HOME="`/usr/libexec/java_home -v '1.8*'`"

	2. Android Studio and SDK

		Download from

		<a href="http://developer.android.com/sdk/index.html">http://developer.android.com/sdk/index.html</a>

		After install on the terminal

			$ vim ~/.zshrc

				export PATH="$PATH:/Users/dragon/Library/Android/sdk/platform-tools:/Users/dragon/Library/Android/sdk/tools:${ANT_HOME}/bin"


	3. Ant

		Download from

		<a href="http://ant.apache.org/bindownload.cgi">http://ant.apache.org/bindownload.cgi</a>

		After install on the terminal

			$ vim ~/.zshrc

				export ANT_HOME="/Users/dragon/Library/apache-ant/apache-ant-1.9.6"

	4. Download Android API

		Open a new terminal and type:

			$ android

		If everything is working correct it will open up the Android SDK Manager.

		Install API 22 and 23 or the most two recent versions with SDK Platforms and Arm Image checked

	5. Configure android emulator

		Open a new terminal and type:

			$ android avd

		Click the create button and add at least 1 device to emulate with this params:

			AVD Name:			Android_Emulator_x86_64
			Device:			Nexus 5 (4.95", 1080 x 1920: xxhdpi)
			Target:			Android 6.0 - Level 23 (The last one)
			CPU/ABI:			Intel Atom (x86_64)
			Keyboard:			Checked HArdware keyboard present
			Skin:				No skin
			Front Camera:			None
			Back Camera:			None
			Memory options:
				RAM:			2048
				VM Heap:			64
			Internal Storage:		200 MiB
			SD Card:
				Size:			None
				File:			None
			Emulation Options:		Checked Use Host GPU

		Click Ok

		Start it to check if it works


2. iOS setup

	1. Install Xcode from app store. This will take awhile since it is ~2 gigs in size

		Once install is completed, open xcode and accept the license

	2. Install the IOS Simulator that Ionic will use.

			npm install -g ios-sim

### Install

####Install Ionic and dependencies

1. Install nodejs and homebrew via: <a href="http://www.johnpapa.net/how-to-use-npm-global-without-sudo-on-osx/">http://www.johnpapa.net/how-to-use-npm-global-without-sudo-on-osx/</a>
   It is better when you have node installed with brew and npm installed on its own, or else, if in trouble with brew and npm, give owner permission to some folders as said it in
<a href="http://stackoverflow.com/questions/18923191/npm-install-fails">http://stackoverflow.com/questions/18923191/npm-install-fails</a>
		sudo chown -R `whoami` ~/.npm
		sudo chown -R `whoami` /usr/local/lib/node_modules

2. Install ionic and its dependencies

		npm install -g cordova
		npm install -g ionic
		npm install -g gulp

	If you get:

				/usr/local/lib
		└── (empty)

		npm ERR! code 1

	Then you must:

		$ sudo chown -R $(whoami):wheel /usr/local/bin
		$ sudo chown -R $(whoami):wheel /usr/local/share

	You should do the last step every time you get an error on installing with npm


### Testing

1. Check android:

		$ ionic add platform android
		$ ionic build android
		$ ionic emulate android

	You must get:

			$ ionic emulate android
			  ...(Output ommited)

			  BUILD SUCCESSFUL

			  Total time: 2.644 secs
			  Built the following apk(s):
			      /Users/Desktop/MyApp/platforms/android/build/outputs/apk/android-debug.apk
			  Installing app on emulator...
			  Using apk:/Users/Desktop/MyApp/platforms/android/build/outputs/apk/android-debug.apk
			  INSTALL SUCCESS
			  Unlocking screen...
			  Launching application...
			  LAUNCH SUCCESS


2. Check iOS

		$ ionic add platform ios
		$ ionic build ios
		$ ionic emulate ios

	You must get:

			$ ionic emulate ios
			  ...(Output ommited)

			  ** BUILD SUCCEEDED **

			  No target specified for emulator. Deploying to iPhone-6 simulator
			  com.ionicframework.starter: 73300
			  ** RUN SUCCEEDED **


### Conclusion
Ionic works in its version stable. Versions nightly and alpha won't work. So don't do this:

	$ npm install -g alpha@ionic


### Authors:
Nadir Palacios

<a href="http://github.com/intfrr">http://github.com/intfrr</a>

Justin James

<a href="http://digitaldrummerj.me/ionic-setup-osx/">http://digitaldrummerj.me/ionic-setup-osx/</a>

Dara Bun

<a href="http://dara.azurewebsites.net/ionic-android-osx/">http://dara.azurewebsites.net/ionic-android-osx/</a>

The ionic team

<a href="http://ionicframework.com/docs/guide/testing.html">http://ionicframework.com/docs/guide/testing.html</a>


