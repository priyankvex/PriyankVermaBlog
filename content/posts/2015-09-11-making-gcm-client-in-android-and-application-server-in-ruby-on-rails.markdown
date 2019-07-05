---
author: priyankvex
date: 2015-09-11 19:17:16+00:00
draft: false
title: Making GCM client in Android and Application server in Ruby on Rails
type: post
url: /2015/09/11/making-gcm-client-in-android-and-application-server-in-ruby-on-rails/
tags:
- android
- Application
- cloud
- gcm
- google
- java
- messaging
- rails
- ror
- ruby
---

It is always fun to play with new APIs and tools. GCM is not something I was getting my hands on for the first time but it changed completely since last time I did a project using this.

But the good news is it has changed for good. New service classes makes it easier to write GCM clients for Android, GCM default configuration makes writing test servers and apps to play with very less tedious. In fact my first reaction was _**this is GCM reincarnated. **_

[caption id="attachment_163" align="aligncenter" width="640"][![GCM Client and App server](https://priyankvex.files.wordpress.com/2015/09/gcm_stack.png)
](https://priyankvex.files.wordpress.com/2015/09/gcm_stack.png) GCM Client and App server[/caption]

**New API : New Party!**

You can have a look at the source code here :

[https://github.com/priyankvex/GCM-Android-Client-and-Rails-Server](https://github.com/priyankvex/GCM-Android-Client-and-Rails-Server)

To create Android client I stuck with sample provided in the docs. Sweet and simple to implement. Just little tweaks done to make it fit my needs.

For creating application server i.e the 3rd party server required by the GCM stack, it used Ruby on Rails. In that specifically I used "_**gcm**_" _**gem**_.

Again not a very complex server but good enough to get a hold of things.

**Server features : **



	  1. Save incoming device tokens (registration ids).
	  2. Web form to send message to all devices registered.
	  3. Send welcome notification when device is registered.

**Client features (Android App) :**



	  1. Get GCM token for the device.
	  2. Send token to applications server.
	  3. Show notification when message is pushed from server.


