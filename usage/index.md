# Usage and workflow

tarifa commands may be splitted into the following categories:

### build and development tasks

* `prepare` launches the www project builder and copy/links it to the cordova app.
* `build` execute the cordova build chain (prepare and compile) with hooks allowing
changes, such as the name of the app...
* `run` run the app on the connected devices, will ask which one if more than
one is available.
* `check` check the current tarifa project after clone or host switch.
* `clean` cleans project.

### project management tasks

* `create` interactively creates a tarifa project.
* `platform` manages platforms.
* `plugin` manages plugins.
* `info` gets general data on your host and attached devices.
* `config` configures graphical assets and provisioning files.

### deploy tasks

* `hockeyapp` beta deployment with hockeyapp.
