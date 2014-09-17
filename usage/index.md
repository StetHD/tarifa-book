# Usage and workflow

tarifa commands may be splitted into the following categories:

### build and development tasks

* `prepare` launch the www project builder and copy/link it to the cordova app.
* `build` execute the cordova build chain (prepare and compile) with hooks allowing
changes, like the name of the app...
* `run` run the app onto the connected devices, will ask which one if more than
one is available.
* `check` check current tarifa project after clone or host switch.
* `clean` clean project.

### project management tasks

* `create` interactively create a tarifa project.
* `platform` manage platforms.
* `plugin` manage plugins.
* `info` get general data on your host and attached devices.
* `config` configure graphical assets and provisioning files.

### deploy tasks

* `hockeyapp` beta deployment with hockeyapp.
