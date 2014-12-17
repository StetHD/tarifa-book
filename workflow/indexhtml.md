# Workflow

the main tarifa workflow:

```
 +----------------------+
 |     configuration    |   the user chooses a configuration
 +----------------------+
             |
             v
 +----------------------+
 |        prepare       |   calls the front-end project build
 |           |          |   with the given configuration
 |           v          |   and symlinks/copies output to cordova www
 |+--------------------+|
 ||project/bin/build.js||
 |+--------------------+|
 +----------------------+
             |
             v
 +----------------------+
 |         build        |   tarifa build tasks + cordova compile
 +----------------------+
             |
             v
 +----------------------+
 |          run         |   tarifa tasks + cordova run
 +----------------------+

```

Each step has a command: [`tarifa prepare`](../usage/prepare.md), [`tarifa build`](../usage/build.md) and [`tarifa run`](../usage/run.md).

The **build** step executes the following extra tasks:

**Global tasks**

* change cordova's `config.xml` according to the configuration
* copy the configuration's icons
* copy the configuration's splash screens
* clean the given platform
* reset `config.xml`

**wp8 tasks**

* change the assembly info
* change the manifest
* change the `.csproj` file
* run XapSignTool to sign app for Company app distribution

**ios tasks**

* change product file name
* change bundleId
* set code sign identity for signing app
* run xcrun for signing app

**android tasks**

* clean output folder
* change app activity
* change release properties file
* change app label
* copy apk
