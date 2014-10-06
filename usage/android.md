# Android

### Configuration attributes

As with the ios platform, any android configuration needs at least the following
3 attributes in the `tarifa.json` file:

``` json
{
  "id": "the.javapackage.name",
  "product_name": "final app name",
  "product_file_name": "name_of_generated_apk_file"
}
```

* `id` the java package of the application.
* `product_name` the final app name which is shown on your devices' OS.
* `product_file_name` the name of the compiled .apk file.

### Release

To build the project in release mode, you need to tell tarifa where to find the
keystore and the alias you want to use for signing the apk file. Each configuration
with the `keystore_path` and `keystore_alias` attributes will be signed and built
in release mode. Usually this is stored in the `private.json` file:

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

In addition to signing the apk, on android, you need to bump the `android:versionCode`
attribute of the `AndroidManifest.xml` file.
Specifying a `version_code` attribute in a configuration will be reflected in the
`AndroidManifest.xml` file.

### Deploy with hockeyapp

In order to deploy a configuration on hockeyapp, you need to add the `hockeyapp_id`
to the given configuration. For example in a `private.json` file:

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
