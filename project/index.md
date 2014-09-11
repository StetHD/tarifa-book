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

A tarifa project is composed of 3 folders:

* `app` folder with the cordova app
* `images` folder containing all icons and splashscreens
* `project` folder containing the www project

and 2 json files:

* `tarifa.json` containing a commitable definition of the project
* `private.json` containing all private informations needed to deploy or sign the apps.

### the raw cordova app

The content of the `app` folder is a normal cordova app that should be extractable from the project.
Right now, the tarifa build process still change settings in the cordova app without undoing them. This still need to be done.

During the build process tarifa will copy or link the output of  the `www` project folder to `app/www`.

Right now tarifa just wrapps cordova plugins without any extra features.

### www project

It's a regular front-end project with the build system you want satisfying the following interface:

* have a `bin/build.js` node module exposing a function launching the build process
* generate output in a folder name `www`

The `bin/build.js` module have the following signature:

``` javascript
var Q = require('q');

module.exports = function (platform, settings, configurationName) {
    // do async stuff then
    return Q.resolve();
}
```

 where

* `platform` is the platform choosen by the user
* `settings` is a object containing all project settings (merged `tarifa.json` and `private.json` objects)
* `configurationName` is the configuration name choosen by the user for the current build

In the default tarifa project template, browserify is used in order to embed the configuration settings as
a global module named `settings` that you can require in your js code.

### `tarifa.json` and `private.json`

Those two files are the description of a tarifa project and contains all needed
informations from configurations definitions to keystore paths. `tarifa.json` is the
main description and `private.json` contains all not commitable stuff like apple id or hockeyapp token.

#### `tarifa.json`

the squeleton of a minimal `tarifa.json` file:

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

##### attributes

###### `name`
It's the default app name, it the name used to create the cordova project on `tarifa create`. <span style="background:yellow;"><strong>FIXME</strong> Can't be changed right now.</span>

###### `id`
It's the default cordova id. **_FIXME_** Can't be changed right now.

###### `description`
It's a brief description of the app, it' will be replaced in the corodva `config.xml`

###### `version`
It's the default version of the project and it's possible to overwrite it in a configuration. It must be a 3 digits style version number. On
windows phone and windows8, 4 digits are mandatory, tarifa will append a `.0` to the version to match their spec. **_FIXME_** Still no validation in the version format.

###### `platforms`

It's a list of all available platforms in the tarifa project.

###### `plugins`

It's a list of all installed cordova plugins in the tarifa project.

###### `configurations`

It's a definition of all available configurations. While creating a project with `tarifa create`, tarifa will add 4 defaults configurations for each platforms you want: **_default_**, **_dev_**, **_stage_** and **_prod_**.

For example, on a project with only the web and the android platform, by default `configurations` should look like that:

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

Each platforms have a set of configurations name with and a minimum of 3 attributes:

* `id` which allows to overwrite the default cordova app `id`
* `product_name` which allows to overwrite the name of the app, the one you read on your device screen
* `product_file_name` which allows to specify the name of the generated binary (in the case of android an .apk file)

###### `cordova`

It contains a `preferences` attributes allowing to overwrite any cordova `config.xml` preferences and a `accessOrigin` attributes.
By default `tarifa create` will generate the content of the `cordova` attribute like that:

###### `author`

The `author` defines the following properties:

```json
{
  "name": "your name",
  "email": "me@tarifa.tools",
  "href": "http://tarifa.tools"
}
```


#### `private.json`

The `private.json` contains all not commitable configurations informations. On a project with only the android platform and only handling the siging
process of an apk, the `tarifa.json` file would looks like:

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

Defining `keystore_path` and `keystore_alias` in a configuration tells tarifa to compile this android configuration in release mode and to sign it with
the given key alias and key store.
