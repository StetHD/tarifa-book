# Usage

tarifa commands may be splitted into the following categories:

### build and development tasks

* [`prepare`](./prepare.md) launches the www project builder and copy/links it to the cordova app.
* [`build`](./build.md) execute the cordova build chain (prepare and compile) with hooks allowing
changes, such as the name of the app...
* [`run`](./run.md) run the app on the connected devices, will ask which one if more than
one is available.
* [`watch`](./watch.md) run the app in live reload mode
* [`check`](./check.md) check the current tarifa project after clone or host switch.
* [`clean`](./clean.md) cleans project.

### project management tasks

* [`create`](./create.md) interactively creates a tarifa project.
* [`platform`](./platform.md) manages platforms.
* [`plugin`](./plugin.md) manages plugins.
* [`info`](./info.md) gets general data on your host and attached devices.
* [`config`](./config.md) configures graphical assets and provisioning files.
* [`update`](./update.md) update default cordova plugins and cordova platforms.

### deploy tasks

* [`hockeyapp`](./hockeyapp.md) beta deployment with hockeyapp.
