# Usage

tarifa commands may be splitted into the following categories:

### project management tasks

* [`create`](./create.md) interactively creates a tarifa project (or a cordova plugin).
* [`info`](./info.md) gets general data on your host and attached devices.
* [`config`](./config.md) configures graphical assets and provisioning files.
* [`platform`](./platform.md) manages platforms.
* [`plugin`](./plugin.md) manages plugins.
* [`update`](./update.md) updates default Cordova plugins and Cordova platforms.

### build and development tasks

* [`prepare`](./prepare.md) launches the www project builder and copies/links the www folder to the Cordova app.
* [`build`](./build.md) executes Cordova's build chain (prepare and compile) and tarifa's extra tasks.
* [`run`](./run.md) runs the app on the connected devices, will ask which one if more than
one is available.
* [`watch`](./watch.md) runs the app in live reload mode.
* [`check`](./check.md) checks the current tarifa project after clone or host switch.
* [`clean`](./clean.md) cleans the project.

### deploy tasks

* [`hockeyapp`](./hockeyapp.md) deploys the app to HockeyApp.
