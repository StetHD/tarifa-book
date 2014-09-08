# Install

You can install tarifa on windows, linux or macosx. First you need a working
[node.js](http://nodejs.org/) environment.

Depending on your host, you will be able to support the following platforms:

| platform/os                                | macosx | linux | win32 |
| -------------------------------------------|:------:| -----:| -----:|
| [ios](http://developer.apple.com/)         | ✔      | ✗     | ✗     |
| [android](http://developer.android.com/)   | ✔      | ✔     | ✔     |
| windows phone                              | ✗      | ✗     | ✔     |
| windows8                                   | ✗      | ✗     | ✔     |

You need to install the needed sdk in order to work with a given platform.

all hosts need [ImageMagick](http://www.imagemagick.org/) for icons and splashscreens generations.
[cupertino](https://github.com/nomad/cupertino) from nomad cli is needed on macosx in order to manage mobile provisioning files.

Install tarifa cli with npm:

```
npm install -g tarifa
```

Some optional dependencies should failed depending on your os
(like, cordova-deploy-windows-phone fails to install on linux or mac os x).

## Macosx
TODO fast install notes for
* ios
* android
* wp8 with a vm
* windows8 with a vm

## Linux
TODO fast install notes for
* android

## Windows
TODO fast install notes for
* android
* wp8
* windows8
