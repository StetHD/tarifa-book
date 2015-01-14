# Workflow

the main tarifa workflow:

```
          +-------------------------+
          |  chosen configuration   |
          +-------------------------+
                       |
                       v
 +-------------------------------------------+
 |        +-------------------------+        |
 |        |   project/bin/build.js  |        |
 |        +-------------------------+        |   tarifa prepare: call the front-end project build +
 |                     |                     |                   copy/symlink output to cordova www
 |                     v                     |
 |            copy/symlink output            |
 +-------------------------------------------+
                       |
                       v
 +-------------------------------------------+
 |            pre-cordova-prepare            |
 |                     |                     |
 |                     v                     |
 |        +-------------------------+        |
 |        |     cordova prepare     |        |
 |        +-------------------------+        |
 |                     |                     |
 |                     v                     |
 |            pre-cordova-compile            |   tarifa build: our tasks +
 |                     |                     |                 cordova prepare & compile
 |                     v                     |
 |        +-------------------------+        |
 |        |     cordova compile     |        |
 |        +-------------------------+        |
 |                     |                     |
 |                     v                     |
 |            post-cordova-compile           |
 +-------------------------------------------+
                       |
                       v
             +-------------------+
             |        run        |               tarifa run: our tasks + cordova run
             +-------------------+

```

Each step has a command: [`tarifa prepare`](../usage/prepare.md), [`tarifa build`](../usage/build.md) and [`tarifa run`](../usage/run.md).

The **tarifa build** step executes the following extra tasks at the `pre-cordova-prepare`, `pre-cordova-compile` and `post-cordova-compile` stages:

**Shared tasks**

* change Cordova's `config.xml` according to the configuration
* copy the configuration's icons
* copy the configuration's splash screens
* clean the given platform
* reset `config.xml`

**WP8 specific tasks**

* change the assembly info
* change the manifest
* change the `.csproj` file
* run XapSignTool to sign app for Company app distribution

**iOS specific tasks**

* change product file name
* change bundleId
* set code sign identity for signing app
* run xcrun for signing app

**Android specific tasks**

* clean output folder
* change app activity
* change release properties file
* change app label
* copy apk
