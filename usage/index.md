# Usage and workflow

tarifa commands are splitted in the following categories.

### build and developpement tasks

* `prepare` launch the www project builder and copy/link it to the cordova app
* `build` executing the cordova build chain (prepare and compile) with some hooks
allowing some change, like the name of the app, ...
* `run` run the app on your connected devices, will ask which one if more than one is available
* `check` check current tarifa project after clone or host switch
* `clean` clean project

### project management tasks

* `create` create interactively a tarifa project
* `platform` manage platforms
* `plugin` manage plugins
* `info` get general informations on your host and attached devices
* `config` configure graphical assets and provisioning files

### deploy tasks

* `hockeyapp` beta deployement with hockeyapp
