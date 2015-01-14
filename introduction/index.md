# Introduction
#### Why wrapping Apache Cordova with another CLI?

Using Apache Cordova means having basic knowledge of each platform you work with:

* how to build and debug the *common* way (with an IDE like Xcode, Visual Studio...)
* release and publish your app to stores (iOS, Android, WP...)
* how to sign and distribute your app to testers (HockeyApp, iOS ad-hoc distribution...)

You may need to change or add stuff in the native part of your Apache Cordova project
depending on the platform. For example, to produce a signed Android APK, you need
to add a `release.properties` file containing the path to the keystore and the
keystore alias. Or on iOS, to produce a signed IPA for adhoc distribution, you need to
change the `CODE_SIGN_IDENTITY` in your `build-release.xcconfig` file if you have multiples identities.

Tarifa aims at taking care of all the little things you need to know/do to build
a Cordova app, so you can focus on creating content. We started the
project with the idea of making a practical tool for our dev team and to
lower the barrier of development and project sharing with Cordova.

Finally, tarifa introduces [configurations](../configurations/index.md). These are
an important concept as they modify the output of each command; they
allow to create multiple versions of the same application on a given
platform (one for each environment), which can for example be useful for white-label apps.
