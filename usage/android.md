# Android

## Configuration attributes

like the ios platform any android configuration needs at least those 3 following attributes in the `tarifa.json` file:

``` json
{
  "id": "the.javapackage.name",
  "product_name": "final app name",
  "product_file_name": "name_of_generated_apk_file"
}
```

* `id` is the java package of the application.
* `product_name` is the final app name, the one you read on the screen
* `product_file_name` is the name of the compiled .apk file

## Release

To build the project in release mode, you need to tell tarifa where to find the keystore and the alias
you want to use for signing the apk file. Each configuration having the both following attributes will be signed and
build in release mode. Usually, this informations are stored in the `private.json` file:

```json
{
  "configurations": {
    "android": {
      "prod": {
        "keystore_path": "path/to/my.keystore",
        "keystore_alias": "mykeystorealias"
      }
    }
  }
}
```

In addition of signing the apk, on android, you need to bump the `android:versionCode` attributes of `AndroidManifest.xml` file.
Specifying an `version_code` attributes in a configuration will be reflected in the `AndroidManifest.xml` file.

## Deploy with hockeyapp

In order to deploy a configuration on hockeyapp, you need to add the `hockeyapp_id`
to the given configuration. for example in a `private.json` file.

``` json
{
  "configurations": {
    "android": {
      "stage": {
        "hockeyapp_id": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
      }
    }
  }
}
```
