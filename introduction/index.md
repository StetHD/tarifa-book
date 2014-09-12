# Introduction
#### Why wrapping cordova with another cli?

Working with cordova involves that you know enough about each platforms you work with:

* how to build/debug the *common* way (with an IDE like Xcode, Visual Studio, ...)
* how to build for release and publish the app to a store (iOS, Android, WP, Windows8, ...)
* how to distribute your app to your testers (hockeyapp, iOS ad-hoc distribution)

You may also need to change or add stuff in the native part of the cordova project
depending on the platform. For example, to update an Android app, you need to
bump the integer value of `android:versionCode` attribute in the `AndroidManifest.xml` file.
Or with iOS, adding a custom url scheme is only possible by adding some values
in the Xcode project plist, cordova do not take care of it in the `config.xml` file.

Tarifa aims to take care of all those little things you need to know/do to build
a cordova app, so you can concentrate on making the content. We started the
project with the idea of making a practical tool for our dev teams and and to
lower the barrier of cordova development and projects sharing.

Finally, tarifa introduces [configurations](../configuration/index.md). Those are
an important concept in tarifa as they modify the output of each command; they
allow for instance to create multiple versions of the same application on the
same platform (one for each environment), which is currently pretty hard to
achieve with cordova.
