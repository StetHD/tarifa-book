### Introduction

Why wrapping cordova with another cli?

Working with cordova means knowing enough about each platforms you work with, which means:

* how to build the *common* way (with an ide)
* how to build a release
* how to publish an app to the store
* how to distribute your app to your tester

Not everythings is perfect and you will always need to change some specifics files in the native project
depending on the platform. The simplest examples: on android, the app have a versionCode attribute in it AndroidManifest.xml
file. This attributes must be bumped each time a new binary is uploaded to the play store.

tarifa aims to take care of all this little things so that you can concentrate in building the app, not the infrastructure.

At the end of the project, the client may want to change the name of the project, with tarifa, it will cost no time.

Renaming a project should not be a nightmare.

The goal of tarifa is to allow an easy developpement and maintenance of cordova apps.
