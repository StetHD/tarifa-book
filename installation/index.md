# Installation

You can install tarifa on Windows, Mac OS X or Linux. You need a working
[node.js](http://nodejs.org/) environment.
It is recommended to install node via [nvm](https://github.com/creationix/nvm).

Depending on your host, you will be able to support the following platforms:

| platform/os                                | macosx | linux | win32 |
| -------------------------------------------|:------:|:-----:|:-----:|
| [iOS](http://developer.apple.com/)         | ✔      | ✗     | ✗     |
| [Android](http://developer.android.com/)   | ✔      | ✔     | ✔     |
| [Windows Phone](http://dev.windows.com/en-us/develop/download-phone-sdk) | ✗      | ✗     | ✔     |

You need to install the proper SDK in order to work with a given platform.

All the OS need [ImageMagick](http://www.imagemagick.org/) for icons and splash screens generation.
tarifa needs [cupertino](https://github.com/nomad/cupertino) on Mac OS X in order to manage mobile provisioning files and to communicate with
[developer.apple.com](http://developer.apple.com/).

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
