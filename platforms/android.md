# Android

### Configuration attributes

As with the iOS platform, any Android configuration needs at least the following
3 attributes in the [`tarifa.json`](../project/index.md#tarifajson-and-privatejson) file:

``` json
{
  "id": "the.javapackage.name",
  "product_name": "final app name",
  "product_file_name": "name_of_generated_apk_file"
}
```

* `id` the Java package of the application.
* `product_name` the final app name which is shown on your device's OS.
* `product_file_name` the name of the compiled .apk file.
* `release` toggles the release mode, `false` by default.
* `sign` is the signing label.
* `hockeyapp_id` is the id of the app on kockeyapp.
* `versionCode` is usefull to overwrite the `AndroidManifest.xml` versionCode.
* `min_sdk_version` is the `android:minSdkVersion` attribute value of all the `uses-sdk` elements in the `AndroidManifest.xml` file.

### Signing attributes

To build the project in release mode, you need to tell tarifa where to find the
keystore and the alias you want to use for signing the apk file.

Each configuration
with the `sign` and `release` attributes will be signed and built
in release mode with the _signing label_ referenced in `sign`. Usually this is stored in the `private.json` file:

``` json
{
  "signing": {
    "android": {
      "store": {
        "keystore_path": "/my/path/to/keystore.keystore",
        "keystore_alias": "xxxxx",
        "keystore_password": "xxxx",
        "alias_password": "xxxxx"
      }
    }
  }
}
```

* `keystore_path` is the path of the keystore.
* `keystore_alias` is the alias used in the keystore.
* `keystore_password` defines the main keystore password. This attribute is optional.
* `alias_password` defines the alias password. This attribute is optional.

By default, `tarifa create` will add a `store` _signing label_ in the `prod` configuration.
