---
layout: post
title: "how to install ionic and its dependencies"
date: 2015-04-01 12:06:57 +0800
comments: true
categories: 
---
- install node js by Homebrew
```
$ brew doctor
$ brew update
$ brew install node
$ brew install ant
```
- install cordova and ionic by npm
```
$ npm install -g cordova ionic
$ npm install -g ios-sim
```
<!-- more -->
- install XCode and Android
- for android sdk we need to go to [SDK Website](http://developer.android.com/sdk/index.html) and download standalone sdk tools only [file](http://developer.android.com/sdk/index.html#Other)

- next, unpack it and run for install required resources
```
$ android-sdk-macosx/tools/android sdk
```
- finally, create a android virtual device by avd tool
```
$ android-sdk-macosx/tools/android avd
```

- Genymotion is recommanded as android emulator (faster than avd) and do not forget to install virtualbox before installing Genymotion.


- you might also want to change avd location
```
ln -s path/to/my/avd ~/.android/avd
```

- then, let's get start with ionic by sample app
```
$ ionic start todo blank
$ ionic platform add ios
$ ionic platform add android
$ ionic build ios
$ ionic build android
$ ionic emulate ios
$ ionic emulate android # for avd
$ ionic run android # for Genymotion
```