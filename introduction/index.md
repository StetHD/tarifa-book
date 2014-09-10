# Introduction
#### Why wrapping cordova with another cli?

Working with cordova means to know enough about each platforms you work with:

* how to build/debug the *common* way (with an ide like xcode, visual studio, ...)
* how to build a release and publish the app to a store (ios, android, wp, windows8, ...)
* how to distribute your app to your tester (hockeyapp, ios ad-hoc distribution)

You may also need to change or add stuff on the native part of the cordova project depending on the platform. For
example, on android, to update an app, you need to bump the integer value of `android:versionCode` attribute in the `AndroidManifest.xml` file.
Or on iOS, adding a custom url scheme is only possible by adding some values in the xcode project plist, cordova do not take care of it in the `config.xml` file.

tarifa aims to take care of all this little things you need to know/do to build a cordova app, so that you can concentrate on building the content. It was build to first serve as a damn practical tool for me and my team mates to lower the barrier of cordova developpement and projects sharing.
At least, tarifa introduces a notion of configuration to lower the pain of creating multiple versions of the same application on the same platform.
