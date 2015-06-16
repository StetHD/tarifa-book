# Updating an existing project

When you create a project with [tarifa create](../usage/create.md), a hidden `.tarifa.json` file is written to the project's root. That file holds a JSON object composed of two attributes: the `created` attribute stores the version of tarifa used on project creation and the `current` attribute stores the version of tarifa used upon the latest execution of the [`tarifa update`](../usage/update.md) command.

Here is an example `.tarifa.json` file, which reflects a project created with tarifa version **0.2.5** and updated to **0.3.0**:

```json
{
  "current": "0.3.0",
  "created": "0.2.5"
}
```

Right now, when you execute the [`tarifa update`](../usage/update.md) command in an existing tarifa project:

1. Each installed platform, core plugin and user plugin (defined in the `~/.config/configstore/tarifa.yml` user settings file) gets updated to the latest available version. Platforms are removed and the latest versions are installed.
2. The `.tarifa.json` file is overwritten with an updated `current` attribute.

The following cordova plugins are available on `tarifa create` and also get updated:

* cordova-plugin-battery-status
* cordova-plugin-camera
* cordova-plugin-console
* cordova-plugin-contacts
* cordova-plugin-device
* cordova-plugin-device-motion
* cordova-plugin-device-orientation
* cordova-plugin-dialogs
* cordova-plugin-file-transfer
* cordova-plugin-geolocation
* cordova-plugin-globalization
* cordova-plugin-inappbrowser
* cordova-plugin-media
* cordova-plugin-network-information
* cordova-plugin-splashscreen
* cordova-plugin-vibration
* cordova-plugin-file
* cordova-plugin-whitelist

Note that the various tarifa files are not automatically updated, but we provide detailed instructions in tarifa's [CHANGES.md](https://github.com/TarifaTools/tarifa/blob/master/CHANGES.md) file.
