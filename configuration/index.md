# Configuration

In tarifa, a configuration is a json object representing the settings of the app for a particular state of the project,
like for example the staging or the production states. Each configuration is described `tarifa.json` file on the root
of a tarifa project.

When creating a tarifa project with `tarifa create`, tarifa will create the following configurations: **_default_**, **_dev_**, **_stage_**, **_prod_**.
You can add or delete any configuration you like. The **_default_** configuration allows to call tarifa without specifying any name.

By default, the **_stage_** configuration is defined to be used for hockeyapp deployements (and ad-hoc distribution siging process on ios).

These configurations are just naming conventions, you can add any configurations you need and each configuration allows the build an unic app.


## `tarifa.json`

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

### attributes

#### `name`
It's the default app name, it the name used to create the cordova project on `tarifa create`. <span style="background:yellow;"><strong>FIXME</strong> Can't be changed right now.</span>

#### `id`
It's the default cordova id. <span style="background:yellow;"><strong>FIXME</strong> Can't be changed right now.</span>

#### `description`
It's a brief description of the app, it' will be replaced in the corodva `config.xml`

#### `version`
It's the default version of the project and it's possible to overwrite it in a configuration. It must be a 3 digits style version number. On
windows phone and windows8, 4 digits are mandatory, tarifa will append a `.0` to the version to match their spec. <span style="background:yellow;"><strong>FIXME</strong> Still no validation in the version format.</span>

#### `platforms`

It's a list of all available platforms in the tarifa project.

#### `plugins`

It's a list of all installed cordova plugins in the tarifa project.

#### `configurations`

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

#### `cordova`

It contains a `preferences` attributes allowing to overwrite any cordova `config.xml` preferences and a `accessOrigin` attributes.
By default `tarifa create` will generate the content of the `cordova` attribute like that:

#### `author`

The `author` defines the following properties:

```json
{
  "name": "your name",
  "email": "me@tarifa.tools",
  "href": "http://tarifa.tools"
}
```


## `private.json`

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
