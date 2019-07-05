---
author: priyankvex
date: 2015-10-06 14:06:02+00:00
draft: false
title: Rails Number Helper Port to Android
type: post
url: /2015/10/06/rails-number-helper-port-to-android/
tags:
- android
- android studio
- helper
- java
- number
- programming
- rails
---

A polyglot developer will understand, there is always something you like about one language and you wish was available for another language too.

So, recently I started learning rails and found _number_helper _API very cool and fun to use. It gives you easy API to convert numbers into many formats like _number_to_human _which will convert 20000 to _20 Thousands _or number_to_human_size that will convert 1024 to 1 KB.

That was it I wanted this stuff for Android too. It just makes processing numbers to fit the UI needs so damn easy.

Here is my attempt to port this rails module to Android.

Here is the source code :

[https://github.com/priyankvex/Rails-Number-Helper-For-Android](https://github.com/priyankvex/Rails-Number-Helper-For-Android)

**Usage : **

Just copy the module _number_helper _in your application folder and include module dependency.

**Examples : **



    
    <code>
    	// Number to human converter
    	NumberToHumanConverterBuilder builder2 = new NumberToHumanConverterBuilder(123456);
    	NumberToHumanConverter converter2 = builder2.build();
    	try {
    	    String humanNumber = converter2.convert();
    	    // OUTPUT : 123.456 Thousands
    	    Log.d(Config.TAG, humanNumber);
    	} catch (InvalidSeparatorException | InvalidDelimiterException
    		| InvalidPrecisionException e) {
    	    e.printStackTrace();
    	}
    </code>


Examples can be found here.
[https://github.com/priyankvex/Rails-Number-Helper-For-Android/blob/master/app/src/main/java/com/wordpress/priyankvex/numberhelperdemo/MainActivity.java](https://github.com/priyankvex/Rails-Number-Helper-For-Android/blob/master/app/src/main/java/com/wordpress/priyankvex/numberhelperdemo/MainActivity.java)

**Features : **



	  * Easy to use API.
	  * High utility for UI needs.
	  * Small in size.
	  * Custom exceptions to fit the needs of Android.


