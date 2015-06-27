---
layout: post
title: "Signing and making an android build for release"
modified:
categories: blog
excerpt:
tags: [Androd, Code-signing]
image:
  feature:
date: 2015-06-27T15:39:55-04:00
comments: true
---

Hello!

Today I am going to talk about how to make an android build in release mode and sign it to submit on [Google play](https://play.google.com/).

### Introduction
If you want to make a build to push over google play then you have to follow these steps:

* Make a build in release mode by running ``` cordova build android --release ```
* Create a code signing key for android.
* Signing that build
* Verify that your APK is signed
* Align the final APK package using zipalign.

Now here is the details explanation about above steps:

###Make a build in release mode by running
Just go inside your application's directory and run command
 {% highlight ruby %}
cordova build android --release
#=> This will create an apk named application_name-release.-unsign.apk inside your build directory.
 {% endhighlight %}

###Create a code signing key
To create a code signing key run command
 {% highlight ruby %}
 keytool -genkey -v -keystore my-release-key.keystore -alias alias_name -keyalg RSA -keysize 2048 -validity 10000
#=> my-release-key.keystore is the name of your keystore file.
#=> alias_name is alias name for your keystore file.
#=> keyalg is algo to code sign.
#=> keysize id the size of key generally it 2048 or bigger than 2048.
#=> validity is validity of key in days.
{% endhighlight %}

###Signing release build
Now sign your build by running the command
{% highlight ruby %}
jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my-release-key.keystore my_application.apk alias_name
#=> my-release-key.keystore is location of your keystore file with name.
#=> my_application.apk is location of your apk with name.
{% endhighlight %}

###Verify apk
Run command
{% highlight ruby %}
 jarsigner -verify -verbose -certs my_application.apk
{% endhighlight %}

###Align the final APK package using zipalign
Run command 
{% highlight ruby %}
zipalign -v 4 your_project_name-unaligned.apk your_project_name.apk
#=> your_project_name-unaligned.apk is your apk which you signed.
#=> your_project_name.apk is the name of the final signed apk which will be generate after this command
{% endhighlight %}

[zipalign](http://developer.android.com/tools/help/zipalign.html) ensures that all uncompressed data starts with a 
particular byte alignment relative to the start of the file, which reduces the amount of RAM consumed by an app.


Now you have a android build in released mode. You can upload it to [Google play](https://play.google.com/).

Note: Please backup your keystore file because if you lost it then no way to recover it. If you want to upload the new 
version of an your application over google play then your new apk must be signed by the same key.
