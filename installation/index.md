# Installation

You can install tarifa on windows, linux or macosx. First you need a working
[node.js](http://nodejs.org/) environment.

Depending on your host, you will be able to support the following platforms:

| platform/os                                | macosx | linux | win32 |
| -------------------------------------------|:------:|:-----:|:-----:|
| [ios](http://developer.apple.com/)         | ✔      | ✗     | ✗     |
| [android](http://developer.android.com/)   | ✔      | ✔     | ✔     |
| [windows phone](http://dev.windows.com/en-us/develop/download-phone-sdk) | ✗      | ✗     | ✔     |
| [windows8](http://dev.windows.com/en-us/develop/downloads) | ✗      | ✗     | ✔     |

You need to install the proper SDK in order to work with a given platform.

All OS need [ImageMagick](http://www.imagemagick.org/) for icons and splash screens generation.
[cupertino](https://github.com/nomad/cupertino) from nomad cli is needed on
macosx in order to manage mobile provisioning files and to talk to
[developer.apple.com](http://developer.apple.com/).

On windows you'll have to ensure that the [PowerShell execution policy](http://technet.microsoft.com/library/hh847748.aspx)
is not set to `Restricted` nor `AllSigned`. A good value for tarifa is setting the policy to `RemoteSigned` for the
`CurrentUser` scope and this can be achieved by running
`Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` as an administrator in some PowerShell.

When the SDKs are properly installed you can install tarifa with *npm*:

```
npm install -g tarifa
```

Some optional dependencies may fail depending on your OS
(like, cordova-deploy-windows-phone fails to install on linux or macosx).