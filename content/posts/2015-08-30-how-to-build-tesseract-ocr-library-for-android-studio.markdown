---
author: priyankvex
date: 2015-08-30 10:07:28+00:00
draft: false
title: How to build Tesseract OCR library for Android Studio?
type: post
url: /2015/08/30/how-to-build-tesseract-ocr-library-for-android-studio/
tags:
- android
- android studio
- build
- OCR
- programming
- Tesseract
---

[Star On GitHub](https://github.com/priyankvex/Easy-Ocr-Scanner-Android)


If you ever tried to create an OCR app for Android you must have stumbled upon the OCR library by Google Tesseract. And then the problems began.

To use the library in your project you first need to build it. But building the library to be compatible with gradle, which is the new build system for Android projects is little not so easily stated anywhere in the library manual.

When I tried to build the library, it took me freaking 9 hours to figure all the how tos?

So, here I am helping you to save your precious hours. (Don't waste these watching late night infomercials for god's sake! ).

**Here we go.**

**Step 1 : **

The first step. Download the NDK. That is used to build the library.

Download it from [here](https://developer.android.com/ndk/downloads/index.html). It is around 300+ MB so keep your net plan nourished.

**Step 2 : **

Better way to go is to use  a fork of Tesseract, Tess-Two. Tess-Two can be found on [GitHub](https://github.com/rmtheis/tess-two).

Execute following commands to build the library Tess-Two using NDK.

    
    <code>
    git clone git://github.com/rmtheis/tess-two tess
    cd tess
    cd tess-two
    ndk-build
    android update project --path .
    ant release
    </code>


We can live without building eyes-two for this time.

Building will take few minutes. After you have successfully built tess-two, give yourself a little treat. You are almost done.

**Step 3 :**

Now you are ready to use the library in your Android project.

Copy the tess-two folder (tess/tess-two), in the main folder of the application project.

Suppose name of your application is "MyApp" copy the folder at "MyApp/".

**Step 4 :**

Now its time to play the trick. The library was build using ANT. But Android projects use Gradle these days. Interesting...

We need to add a "build.gradle" file at location "tess-two/".

The build file can be found [here](https://github.com/priyankvex/Easy-Ocr-Scanner-Android/blob/master/easy_ocr_library/libs/tess-two/build.gradle).

Then include following line in project.settings file.

    
    <code>include ':tess-two'</code>


**Step 5 : **

Build the project and you are just one step away from being done.

**Step 6 : **

The most important step. After completing steps 1-5, _**throw your hands up in the air! **_:D :D You are now done!

Ready to harness the power of OCR.




[https://buttons.github.io/buttons.js](https://buttons.github.io/buttons.js)
