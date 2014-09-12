# Introduction
#### Why wrapping cordova with another CLI?

To use cordova you must know enough about each platform you work with:

* how to build/debug the *common* way (with an IDE like Xcode, Visual Studio...)
* how to build for release and publish your app to a store (iOS, Android, WP, Windows8...)
* how to distribute your app to testers (hockeyapp, iOS ad-hoc distribution...)

You may also need to change or add stuff in the native part of the cordova project
depending on the platform. For example, to update an Android app, you need to
bump the integer value of the `android:versionCode` attribute in the `AndroidManifest.xml` file.
Likewise, with iOS, adding a custom url scheme is only possible by adding some values
in the Xcode project plist as cordova does not take care of it in the `config.xml` file.

Tarifa aims at taking care of all the little things you need to know/do to build
a cordova app, so you can concentrate on creating actual content. We started the
project with the idea of making a practical tool for our dev teams and to
lower the barrier of development and projects sharing with cordova.

Finally, tarifa introduces [configurations](../configuration/index.md). These are
an important concept in tarifa as they modify the output of each command; they
allow for instance to create multiple versions of the same application on a given
platform (one for each environment), which is currently pretty hard to achieve
with cordova.
