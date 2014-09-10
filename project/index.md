# Anatomy of a tarifa project

A tarifa project `example` looks like that:

```
example
|-- app
|   |-- config.xml
|   |-- hooks
|   |-- merges
|   |-- platforms
|   |-- plugins
|   `-- www
|-- images
|-- project
|   |-- bin
|   |   |-- build.js
|   |   `-- mapping.json
|   |-- package.json
|   `-- www
|-- tarifa.json
`-- private.json
```

You can see the cordova project in the `app` folder. The `images` folder is the
collection of icons and splashscreens needed for the project. The `project` folder
is the `www` folder project builder (you can see it just as a very common front-end project).
The `tarifa.json` and `private.json` files are the definition of the project.

### the raw cordova app

The raw cordova app is located in the `app` folder, it remains a normal cordova app that could be extracted from the project.
Right now, the tarifa build process still change settings in the cordova app without undoing them. This still need to be done.
On win32, the `www` project folder is copied to `app/www`, on other os, it's just a link.

For now tarifa just wrapps cordova plugins without any extra features.

### www project

It's a regular front-end project with the build system you want with the following interface:

* have a `bin/build.js` node module exposing a function to launch the www build process
* generate output in a `www` folder

The `bin/build.js` node will be used by tarifa during the build process and have the
following signature:

``` javascript
var Q = require('q');

module.exports = function (platform, settings, configurationName) {
    // do async stuff then
    return Q.resolve();
}
```

* `platform` is the platform choosen by the user
* `settings` is a object containing all project settings
* `configurationName` is the configuration name choosen by the user for the current build

In the default tarifa project template, browserify is used in order to embed the configuration settings as
a global module named `settings` that you can require.

### tarifa.json and private.json files

those two files are the description of a tarifa project and contains all needed
informations from configurations definitions to signing keys. `tarifa.json` is the
main description and `private.json` contains all not commitable stuff like apple ids or
path to keystore and so one.

Here is a `tarifa.json` example:

``` javascript
{
  "name": "myapp", // the default app name (can not be changed right now)
  "id": "org.tarifa.demo", // the default cordova app id (can not be changed right now)
  "description": "a simple app description", // project description
  "version": "1.0.0", // default version of app, it must have a 3 digits format
  "platforms": [
    "android",
    "web"
  ], // available platforms on project
  "plugins": [
    "org.apache.cordova.splashscreen"
  ], // cordova plugins
  "configurations": { // starting definitions of configurations:
    "android": {
      "default": {
        // we can overwrite the default values
        "id": "org.tarifa.demo",
        // the product name is the final name of the app, the one
        // you read on the store
        "product_name": "demo",
        // this is the name of the generated .apk file
        "product_file_name": "demo"
      },
      "dev": {
        "id": "org.tarifa.dev",
        "product_name": "demo dev",
        "product_file_name": "demo",
        // we can overwrite general attributes
        "version": "2222.0.0"
      },
      "stage": {
        "id": "org.tarifa.stage",
        "product_name": "demo stage",
        "product_file_name": "demo",
        "version": "123.0.0"
      },
      "prod": {
        "id": "org.tarifa.demo",
        "product_name": "demo prod",
        "product_file_name": "demo",
        // we can add custom attributes for a given configuration
        "version_code": "1"
      }
    },
    "web": {
      "default": {
        "id": "org.tarifa.demo",
        "product_name": "demo",
        "product_file_name": "demo"
      }/* ,  ... */
    }
  },
  "cordova": { // default cordova settings
    "preferences": {
      "DisallowOverscroll": true,
      "EnableViewportScale": false,
      "KeyboardDisplayRequiresUserAction": false,
      "ShowSplashScreenSpinner": false,
      "HideKeyboardFormAccessoryBar": false,
      "SplashScreen": "screen",
      "AutoHideSplashScreen": true,
      "KeyboardShrinksView": true,
      "KeepRunning": true
    },
    "accessOrigin": [
      "*"
    ]
  },
  "author": {
    "name": "your name",
    "email": "me@tarifa.tools",
    "href": "http://tarifa.tools"
  }
}
```

and the according `private.json` file:

``` javascript
{
  "configurations": {
    "android": {
      "prod": {
        // information needed in order to sign the app in release mode
        // to deploy to store
        "keystore_path": "/path/to/my/key.keystore",
        "keystore_alias": "myalias"
      }
    }
  }
}
```

