# Configurations

In tarifa, a configuration is a json representation of the application settings
for a particular environment. It is described under the `configurations` key in
  the `tarifa.json` file.

When creating a tarifa project with `tarifa create`, tarifa will create the
following configurations: **_default_**, **_dev_**, **_stage_** and **_prod_**.

You can add or delete any configuration you like. The **_default_** configuration
allows to run tarifa commands without specifying an environment. For instance:

    $ tarifa run android

will use the **_default_** configuration to run the app, whereas:

    $ tarifa run android dev

will use the **_dev_** configuration where you can have settings which are specific
to your dev environment.

By default, the **_stage_** environment is configured for hockeyapp deployments
(and ad-hoc distribution signing process on ios as well), but you can change that.

These configurations are just naming conventions. You can add any configuration
you need and each one allows you to build a unique application.

### `tarifa.json`

Here is the skeleton of a minimal `tarifa.json` file:

``` json
{
  "name": "myapp",
  "id": "org.tarifa.demo",
  "description": "a simple app description",
  "version": "1.0.0",
  "platforms": [
    "android",
    "browser"
  ],
  "plugins": [
    "org.apache.cordova.splashscreen"
  ],
  "configurations": {
    "android": {
      "default": {
        "id": "org.tarifa.demo",
        "product_name": "demo",
        "product_file_name": "demo"
      }
    },
    "browser": {
      "default": {
        "id": "org.tarifa.demo",
        "product_name": "demo",
        "product_file_name": "demo"
      }
    }
  },
  "cordova": {
    "preferences": {},
    "accessOrigin": []
  },
  "author": {}
}
```

#### attributes

##### name
The default app name which is chosen when running `tarifa create`. Tarifa will ensure the chosen name is the same as the one defined in the `app/config.xml` file (this must be checked because you may use an existing cordova app folder in a tarifa project and if the names differ tarifa won't run).

##### id
The default cordova id. If you do not overwrite the id in some configuration tarifa will fallback to using this id.

##### description
A brief description of the app, which will be inserted into the cordova `config.xml`
file.

##### version
The version of the project can be overwritten in any configuration. It must
be a 3 digits version number (e.g. `0.0.0`).
On windows phone, 4 digits are mandatory, so tarifa will automatically
append `0` to the specified version.

##### platforms

A list of platforms which are available for the tarifa project.

##### plugins

An object mapping plugin ids to plugin uris like:

```json
{
  "plugins": {
    "org.apache.cordova.splashscreen": "https://github.com/apache/cordova-plugin-splashscreen.git#r0.3.3",
    "org.apache.cordova.console": "https://github.com/apache/cordova-plugin-console.git#r0.2.11"
  }
}
```

##### configurations

A definition of the various configurations. When creating a project with `tarifa create`,
tarifa will add 4 default configurations for each platform you selected: **_default_**,
**_dev_**, **_stage_** and **_prod_**.

For instance, the configuration attribute will look like the following on a project
for which you selected browser and android as platforms:

```json
{
  "android": {
    "default": {
      "id": "org.tarifa.demo",
      "product_name": "demo",
      "product_file_name": "demo"
    },
    "dev": {
      "id": "org.tarifa.dev",
      "product_name": "demo dev",
      "product_file_name": "demo-dev"
    },
    "stage": {
      "id": "org.tarifa.stage",
      "product_name": "demo stage",
      "product_file_name": "demo-stage"
    },
    "prod": {
      "id": "org.tarifa.prod",
      "product_name": "demo prod",
      "product_file_name": "demo-prod"
    }
  },
  "browser": {
    "default": {
      "id": "org.tarifa.demo",
      "product_name": "demo",
      "product_file_name": "demo"
    },
    "dev": {
      "id": "org.tarifa.dev",
      "product_name": "demo dev",
      "product_file_name": "demo-dev"
    },
    "stage": {
      "id": "org.tarifa.stage",
      "product_name": "demo stage",
      "product_file_name": "demo-stage"
    },
    "prod": {
      "id": "org.tarifa.prod",
      "product_name": "demo prod",
      "product_file_name": "demo-prod"
    }
  }
}
```

Each platform has a minimum of 3 attributes:

* `id` allows to overwrite the default cordova app `id`.
* `product_name` allows to overwrite the name of the app: the one you read on your
device's screen.
* `product_file_name` allows to specify the name of the generated binary (in the
case of android, a .apk file).

##### cordova

Contains a `preferences` attribute allowing to overwrite any cordova `config.xml`
preference and an `accessOrigin` attribute.
By default `tarifa create` will generate the contents of the `cordova` attribute
as:

```json
{
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
}
```

##### check

Defines user scripts executed during `tarifa check` for each platform. By default `tarifa create`
will generate:

```json
{
  "check": {
    "android": "./project/bin/check_android.js",
    "ios": "./project/bin/check_ios.js"
  }
}
```

A user script is a node module exporting a function:

``` javascript
module.exports = function (msg) {

    // if async task
    // return Q(msg);
    // else
    return msg;

    // where `msg` is an object with 2 attributes:
    // • the object representing the tarifa.json and the private.json file
    // msg.settings
    // • a boolean
    // msg.verbose
};
```

##### author

Defines the following properties:

```json
{
  "name": "your name",
  "email": "me@tarifa.tools",
  "href": "http://tarifa.tools"
}
```

### `private.json`

Contains configuration data that you do not want to expose in a source control software.

For instance you can use it to set the path to your Android keystore (needed to
sign apps for release):

``` json
{
  "configurations": {
    "android": {
      "prod": {
        "keystore_path": "/path/to/my/key.keystore",
        "keystore_alias": "myalias"
      }
    }
  }
}
```

Defining `keystore_path` and `keystore_alias` in a configuration allows tarifa to
compile this android configuration in release mode and to sign it with the given
key alias and key store.
