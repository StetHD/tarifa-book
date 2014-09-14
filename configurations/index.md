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
(and ad-hoc distribution signing process on ios) as well, but you can change that.

These configurations are just naming conventions, you can add any configuration
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
    "web"
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
    "web": {
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
The default app name which is chosen when running `tarifa create`. <span style="background:yellow;"><strong>FIXME</strong>
Can't be changed right now.</span>

##### id
The default cordova id. <span style="background:yellow;"><strong>FIXME</strong>
Can't be changed right now.</span>

##### description
A brief description of the app, it will be inserted into the cordova `config.xml`
file.

##### version
The version of the project which can be overwritten in any configuration. It must
be a 3 digits version number (e.g. `0.0.0`).
On windows phone and windows8, 4 digits are mandatory, so tarifa will automatically
append `0` to the specified version.

##### platforms

A list of the platforms which are available for that tarifa project.

##### plugins

A list of the currently installed cordova plugins.

##### configurations

A definition of the various configurations. When creating a project with `tarifa create`,
tarifa will add 4 default configurations for each platform you selected: **_default_**,
**_dev_**, **_stage_** and **_prod_**.

For instance, the configurations attribute will look like the following on a project
for which you selected the web and android as platforms:

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
  "web": {
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

Contains configuration data that you don't want to expose in a source control software.

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

Defining `keystore_path` and `keystore_alias` in a configuration tells tarifa to
compile this android configuration in release mode and to sign it with the given
key alias and key store.
