# Workflow

the main tarifa workflow:

```
 +----------------------+
 |     configuration    |   user chooses a configuration
 +----------------------+
             |
             v
 +----------------------+
 |        prepare       |   calls the front-end project build
 |           |          |   with the given configuration
 |           v          |   and symlink/copy output to cordova www
 |+--------------------+|
 ||project/bin/build.js||
 |+--------------------+|
 +----------------------+
             |
             v
 +----------------------+
 |         build        |   /* tarifa build tasks + cordova compile */
 +----------------------+
             |
             v
 +----------------------+
 |          run         |   /* tarifa tasks + cordova run */
 +----------------------+

```

Each step has a command: [`tarifa prepare`](../usage/prepare.md), [`tarifa build`](../usage/build.md) and [`tarifa run`](../usage/run.md).

The **build** step executes the following extra tasks:

**Global tasks**

* _**[global]**_ change the cordova's `config.xml` according to the configuration
* _**[global]**_ copy configurations icons
* _**[global]**_ copy configurations splash screens
* _**[global]**_ clean the given platform
* _**[global]**_ reset `config.xml`

**wp8 tasks**

* _**[wp8]**_ change the assembly info
* _**[wp8]**_ change the manifest
* _**[wp8]**_ change the `.csproj` file
* _**[wp8]**_ run XapSignTool to sign app for Company app distribution

**ios tasks**

* _**[ios]**_ change product file name
* _**[ios]**_ change bundleId
* _**[ios]**_ set code sign identity for signing app
* _**[ios]**_ run xcrun for signing app

**android tasks**

* _**[android]**_ clean output folder
* _**[android]**_ change app activity
* _**[android]**_ change release properties file
* _**[android]**_ change app label
* _**[android]**_ copy apk
