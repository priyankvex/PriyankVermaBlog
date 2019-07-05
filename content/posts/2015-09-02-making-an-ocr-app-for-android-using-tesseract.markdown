---
author: priyankvex
date: 2015-09-02 11:01:58+00:00
draft: false
title: Making an OCR app for Android using Tesseract.
type: post
url: /2015/09/02/making-an-ocr-app-for-android-using-tesseract/
tags:
- android
- android studio
- easy OCR library
- java
- OCR
- programming
- Tesseract
---



[Star on GitHub](https://github.com/priyankvex/Easy-Ocr-Scanner-Android)

Recently I was playing with OCR library by google called as "Tesseract" (cool name for a library!).

[caption id="attachment_153" align="alignleft" width="234"][![App in action.](https://priyankvex.files.wordpress.com/2015/09/screenshot_2015-08-29-23-08-38.png)
](https://priyankvex.files.wordpress.com/2015/09/screenshot_2015-08-29-23-08-38.png) App in action.[/caption]



![Screenshot_2015-08-29-23-08-51](https://priyankvex.files.wordpress.com/2015/09/screenshot_2015-08-29-23-08-51.png?w=480)


















It was a fun experience. This post shows how you can make a simple OCR app in Android using Tesseract.

We will be using [Tess-Two](https://github.com/rmtheis/tess-two) a fork of Tesseract with some additional tools like Liptonica which is an image processing library.

If you want an even easier way to get started with OCR on Android you can try this library built by me. [Easy OCR Library.](https://github.com/priyankvex/Easy-Ocr-Scanner-Android) Usage instructions are in the ReadMe.md file there.

Anyways, moving forward I am using Android Studio on Ubuntu 64 bit machine here.

**Step 1 : **

Clone the library Tess-Two.

    
    <code>
    git clone git://github.com/rmtheis/tess-two tess
    </code>
    


**Step 2 :**

Now we need to build  the library.

For building we will need Android NDK.

    
    <code>
    cd tess
    cd tess-two
    ndk-build
    android update project --path .
    ant release
    </code>
    


Building may take some time so be patient. Don't press ctrl+c too soon :P .

**Step 3  :**

Yay! Time to use the library in Android Project.

Copy the tess/tess-two folder into the root folder of your application project.

**Step 4 : **

In the tess-two folder you just pasted. Add build.gradle file as Android Studio uses gradle build system.

Add following gradle script in the file.

    
    <code>
    buildscript {
        repositories {
    	mavenCentral()
        }
        dependencies {
    	classpath 'com.android.tools.build:gradle:1.2.3'
        }
    }
    
    apply plugin: 'android-library'
    
    android {
        compileSdkVersion 22
        buildToolsVersion "22.0.1"
    
        defaultConfig {
    	minSdkVersion 8
    	targetSdkVersion 22
        }
    
        sourceSets.main {
    	manifest.srcFile 'AndroidManifest.xml'
    	java.srcDirs = ['src']
    	resources.srcDirs = ['src']
    	res.srcDirs = ['res']
    	jniLibs.srcDirs = ['libs']
        }
    }
    </code>
    


**Step 5 : **

Add the following line in project.settings file.

    
    <code>include ':tess-two'</code>


** Step 6 :**

Now we have successfully included the Tess-Two library in our project and we are ready to use it.

First we need to capture the picture itself. You can use something like this code sample taken from [Easy OCR Library](https://github.com/priyankvex/Easy-Ocr-Scanner-Android).

    
    <code>
    public void takePicture(){
    	Intent e = new Intent("android.media.action.IMAGE_CAPTURE");
    	this.filePathOriginal = FileUtils.getDirectory(this.directoryPathOriginal) + File.separator + Calendar.getInstance().getTimeInMillis() + ".jpg";
    	e.putExtra("output", Uri.fromFile(new File(this.filePathOriginal)));
    
    	startActivity(e);
        }
    </code>


Or you can find the code [here](http://labs.makemachine.net/2010/03/simple-android-photo-capture/).

We will also downscale the image a little so that the recognition is fast.

You  can use following code sample from again Easy OCR Library

    
    <code>
     private Bitmap getBitmapFromPath() {
    	BitmapFactory.Options bmOptions = new BitmapFactory.Options();
    	bmOptions.inSampleSize = 4;
    	Bitmap bitmap = BitmapFactory.decodeFile(this.filePath, bmOptions);
    	return bitmap;
        }
    </code>
    


**Step 7 :**

Final step. Recognize the text using the library API.

    
    <code>
     private String scanImage(){
    	TessBaseAPI baseApi = new TessBaseAPI();
    	Log.d(Config.TAG, "Data path : " + FileUtils.getDirectory(this.directoryPath));
    	baseApi.init(FileUtils.getDirectory(this.directoryPath) + "/", this.trainedDataCode);
    	baseApi.setImage(this.mBitmap);
    	String recognizedText = baseApi.getUTF8Text();
    	baseApi.end();
    
    	return recognizedText;
        }
    
    </code>
    


Again I would recommend using the [Easy OCR Library](https://github.com/priyankvex/Easy-Ocr-Scanner-Android) if you are having facing any problem.

That library has many features :



	  1. Very easy setup.
	  2. Handles all the image processing part in a background thread.
	  3. Provides very interface with relative callbacks for the functions of the library.


