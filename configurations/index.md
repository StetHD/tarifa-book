# Configurations

In tarifa, a configuration is a JSON representation of the application settings
for a particular environment. It is described under the `configurations` key in
  the `tarifa.json` file.

When creating a tarifa project with [`tarifa create`](../usage/create.md), tarifa will create the
following configurations: **_default_**, **_dev_**, **_stage_** and **_prod_**.

Aside **_default_**, you can add or delete any configuration you like. The **_default_** configuration
allows to run tarifa commands without specifying an environment. For instance:

    $ tarifa run android

will use the **_default_** configuration to run the app, whereas:

    $ tarifa run android dev

will use the **_dev_** configuration where you can have settings which are specific
to your dev environment.

By default, the **_stage_** environment is configured for [HockeyApp deployments](../usage/hockeyapp.md)
(and ad-hoc distribution signing process on iOS as well) and the **_prod_** one is configured for release and signing process, but you can change that.

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
    "android@3.7.1",
    "browser@3.6.0"
  ],
  "plugins": [
    "org.apache.cordova.splashscreen": "https://github.com/apache/cordova-plugin-splashscreen.git#r0.3.4"
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
The default app name which is chosen when running [`tarifa create`](../usage/create.md). Tarifa will ensure the chosen name is the same as the one defined in the `app/config.xml` file (this must be checked because you may use an existing Cordova app folder in a tarifa project and if the names differ tarifa won't run).

##### id
The default Cordova id. If you do not overwrite the id in some configuration tarifa will fallback to using this id.

##### description
A brief description of the app, which will be inserted into the Cordova `config.xml`
file.

##### version
The version of the project can be overwritten in any configuration. It must
be a 3 digits version number (e.g. `0.0.0`).
On Windows Phone, 4 digits are mandatory, so tarifa will automatically
append `0` to the specified version.

##### platforms

A list of platforms which are available in the project. You can specify an optional version. If you don't tarifa will fetch the latest version available when (re)creating the platform.

```json
{
  "platforms":[
    "android@3.7.1",
    "ios@3.7.0",
    "browser"
  ]
}
```

##### plugins

An object mapping plugin ids to plugin uris or plugin configurations if variables are required:

```json
{
  "plugins": {
    "org.apache.cordova.splashscreen": "https://github.com/apache/cordova-plugin-splashscreen.git#r0.3.3",
    "org.apache.cordova.console": "https://github.com/apache/cordova-plugin-console.git#r0.2.11"
  },
  "com.phonegap.plugins.facebookconnect": {
      "uri": "https://github.com/phonegap/phonegap-facebook-plugin.git#v0.11.0",
      "variables": {
        "APP_ID": "appId",
        "APP_NAME": "appName"
      }
    }
}
```

##### configurations

A definition of the various configurations. When creating a project with [`tarifa create`](../usage/create.md),
tarifa will add 4 default configurations for each platform you selected: **_default_**,
**_dev_**, **_stage_** and **_prod_**.

For instance, the configuration attribute will look like the following on a project
for which you selected browser and Android as platforms:

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

* `id` allows to overwrite the default Cordova app `id`.
* `product_name` allows to overwrite the name of the app: the one you read on your
device's screen.
* `product_file_name` allows to specify the name of the generated binary (in the
case of Android, a .apk file).

##### configurations_mixins

A configuration can be extended from one defined in the `configurations_mixins` attribute by using `extend`.

An example of the extension mechanism in action:

```json
{
  "configurations_mixins": {
    "default": {
      "id": "org.tarifa.demo",
      "product_name": "demo",
      "product_file_name": "demo"
    }
  },
  "configurations": {
    "android": {
      "default": {
        "extend": "default"
      }
    },
    "ios": {
      "default": {
        "extend": "default",
        "product_name": "ios demo",
        "sign": "store"
      }
    }
  }
}
```

Will result in the following configuration:

```json
{
  "configurations": {
    "android": {
      "default": {
        "id": "org.tarifa.demo",
        "product_name": "demo",
        "product_file_name": "demo"
      }
    },
    "ios": {
      "default": {
        "id": "org.tarifa.demo",
        "product_name": "ios demo",
        "product_file_name": "demo",
        "sign": "store"
      }
    }
  }
}
```

You can see the transformed `configurations` by using [`tarifa info`](../usage/info.md) `--dump-configuration` option.

##### cordova

Contains a `preferences` attribute allowing to overwrite any Cordova `config.xml`
preference and an `accessOrigin` attribute.
By default [`tarifa create`](../usage/create.md) will generate the contents of the `cordova` attribute
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
    "*",
    {
      "origin": "tel:",
      "external": true
    }
  ]
}
```

You may also define this attribute in any configuration.

##### check

Defines user scripts executed during [`tarifa check`](../usage/check.md) for each platform.
By default [`tarifa create`](../usage/create.md)
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

##### project_output

Overwrite the default `www` project output folder. It is relative to the project `tarifa.json` file. It is an optional attribute.

##### author

Defines the following properties:

```json
{
  "name": "your name",
  "email": "me@tarifa.tools",
  "href": "http://tarifa.tools"
}
```

##### assets_path

This optional attribute allows you to overwrite the assets directory, which contains the generated images and splashscreens. By default the `images` directory is used.

##### signing

The `signing` attribute defines all _signing labels_ needed in the projet. In a freshly created project it looks like:

``` json
{
  "signing": {
    "ios": {
      "adhoc": {
        "identity": "xxxxxxx",
        "provisioning_path": "/my/file.mobileprovision",
        "provisioning_name": "xxxxxxx"
      },
      "store": {
        "identity": "xxxxxxx",
        "provisioning_path": "/my/file.mobileprovision",
        "provisioning_name": "xxxxxxx"
      }
    },
    "android": {
      "store": {
        "keystore_path": "/my/filekeystore",
        "keystore_alias": "xxxxxxx"
      }
    },
    "wp8": {
      "company_app_distribution": {
        "certificate_path": "/my/file.p12"
      }
    }
  }
}
```

On iOS, each _signing label_ needs the following attributes:
* `identity` defines an apple developer identity.
* `provisioning_path` defines the path of a mobile provisioning file.
* `provisioning_name` defines the name of a mobile provisioning profile.

On android, each _siging label_ needs the following attributes:
* `keystore_path` defines the path of the keystore.
* `keystore_alias` defines the keystore alias.

On wp8, each _siging label_ needs the following attribute:
* `certificate_path` defines the path of the company app distribution certificate.

Adding the `sign` attribute on a configuration allows tarifa to sign the app with the appropriate settings, for example:

```json
{
  "configurations": {
    "android": {
      "prod": {
        "sign": "store",
        "release": true
      }
    }
  }
}
```

will sign the android app with the _signing label_ `store`. The app will be built in release mode as the `release` attribute is set to `true`.

##### deploy

the deploy attributes only contains two attributes needed on ios to communicate with the developer center:

* `apple_id` defines the apple id.
* `apple_developer_team` defines the apple developer team to be used.

Usually, this attribute is placed in the following `private.json` file.

### `private.json`

This JSON file contains data that you do not want to expose in a source control software.

By default, on `tarifa create` the following keys are stored in the `private.json` file:

* [ios] `identity`, the name of the developer identity used to sign an app for distribution.
* [ios] `apple_developer_team`, the apple developer team.
* [ios]`apple_id`, the apple id used to access the provisioning center.
* `token`, the token used to access hockeyapp.
* [wp8] `certificate_path`, the certificate needed to sign the app for company app distribution.

The [platforms section](../platforms/index.html) more thoroughly describes the predefined configuration attributes for all platforms.
