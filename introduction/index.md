# Introduction
#### Why wrapping Apache Cordova with another CLI?

Using Apache Cordova means having basic knowledge of each platform you work with:

* how to build and debug the *common* way (with an IDE like Xcode, Visual Studio...)
* release and publish your app to stores (iOS, Android, WP...)
* how to distribute your app to testers (hockeyapp, iOS ad-hoc distribution...)

You may also need to change or add stuff in the native part of the Apache Cordova project
depending on the platform. For example, to update an Android app, you need to
bump the integer value of the `android:versionCode` attribute in the `AndroidManifest.xml` file.
Likewise, with iOS, adding a custom url scheme is only possible by adding some values
in the Xcode project plist as cordova does not take care of it in the `config.xml` file.

Tarifa aims at taking care of all the little things you need to know/do to build
a cordova app, so you can concentrate on creating actual content. We started the
project with the idea of making a practical tool for our dev team and to
lower the barrier of development and project sharing with cordova.

Finally, tarifa introduces [configurations](../configuration/index.md). These are
an important concept in tarifa as they modify the output of each command; they
allow for instance to create multiple versions of the same application on a given
platform (one for each environment), which is currently pretty hard to achieve
with cordova.
