# Installation

You can install tarifa on Windows, Mac OS X or Linux. You need a working
[node.js](http://nodejs.org/) environment.
It is recommended to install node via [nvm](https://github.com/creationix/nvm).

Depending on your host, you will be able to support the following platforms:

| platform/os                                | macosx | linux | win32 |
| -------------------------------------------|:------:|:-----:|:-----:|
| [iOS](http://developer.apple.com/)         | ✔      | ✗     | ✗     |
| [Android](http://developer.android.com/)   | ✔      | ✔     | ✔     |
| [Windows Phone 8](http://dev.windows.com/en-us/develop/download-phone-sdk) | ✗      | ✗     | ✔|
| browser | ✔      | ✔     | ✔|
| [Firefox OS (experimental)](https://www.mozilla.org/en-US/firefox/os/) | ✔      | ✗     | ✗|

You need to install the proper SDK in order to work with a given platform.

All the OS need [ImageMagick](http://www.imagemagick.org/) to generate icons and splash screens.

On Mac OS X, the following dependencies are needed:
- [cupertino](https://github.com/nomad/cupertino) in order to manage mobile provisioning files and to communicate with [developer.apple.com](http://developer.apple.com/)
- [libimobiledevice](http://www.libimobiledevice.org/) for `tarifa devices`
- [ios-webkit-debug-proxy](https://github.com/google/ios-webkit-debug-proxy) for `tarifa test`
- [ideviceinstaller](http://www.libimobiledevice.org/) for `tarifa test`

On Windows you'll have to ensure that the [PowerShell execution policy](http://technet.microsoft.com/library/hh847748.aspx)
is not set to `Restricted` nor `AllSigned`. A good value for tarifa is setting the policy to `RemoteSigned` for the
`CurrentUser` scope which can be achieved by running
`Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` as an administrator in some PowerShell.

When the SDKs are properly installed you can install tarifa with *npm*:

```
npm install -g tarifa
```

Some optional dependencies may fail depending on your OS
(e.g., cordova-deploy-windows-phone fails to install on Linux or Mac OS X).

Running [`tarifa info`](../usage/info.md) checks if all needed tools are available.
