# Installation

You can install tarifa on Windows, Mac OS X or Linux. You need a working
[node.js](http://nodejs.org/) environment.
It is recommended to install node via [nvm](https://github.com/creationix/nvm).

Depending on your host, you will be able to support the following platforms:

| platform/os                                | macosx | linux | win32 |
| -------------------------------------------|:------:|:-----:|:-----:|
| [iOS](http://developer.apple.com/)         | ✔      | ✗     | ✗     |
| [Android](http://developer.android.com/)   | ✔      | ✔     | ✔     |
| [Windows](https://www.visualstudio.com/products/visual-studio-community-vs) | ✗      | ✗     | ✔|
| browser | ✔      | ✔     | ✔|

You need to install the proper SDK in order to work with a given platform.

All the OS need [ImageMagick](http://www.imagemagick.org/) to generate icons and splash screens.

On Mac OS X, the following dependencies are needed:
- [cupertino](https://github.com/nomad/cupertino) in order to manage mobile provisioning files and to communicate with [developer.apple.com](http://developer.apple.com/)
- [libimobiledevice](http://www.libimobiledevice.org/) for `tarifa devices`
- [ios-webkit-debug-proxy](https://github.com/google/ios-webkit-debug-proxy) for `tarifa test`
- [ideviceinstaller](http://www.libimobiledevice.org/) for `tarifa test`

When the SDKs are properly installed you can install tarifa with *npm*:

```
npm install -g tarifa
```

Some optional dependencies may fail depending on your OS
(e.g., ios-deploy fails to install on Linux or Windows).

Running [`tarifa info`](../usage/info.md) checks if all needed tools are available.
