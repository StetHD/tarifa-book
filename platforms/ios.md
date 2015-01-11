# iOS

### Configuration attributes

In any iOS configuration we need at least the following 3 attributes in the [`tarifa.json`](../project/index.md#tarifajson-and-privatejson) file:

``` json
{
  "id": "the.bundle.id",
  "product_name": "final app name",
  "product_file_name": "name_of_generated_ipa_file"
}
```

* `id` the `bundleid` of the application.
* `product_name` the final app name which is shown on your device's OS.
* `product_file_name` the name of the compiled .ipa file.
* `release` set the release mode, `false` by default.
* `sign` is the signing label.
* `hockeyapp_id` is the id of the app on kockeyapp.

### Signing attributes

Deploying for **ad-hoc** or **store** distribution requires to sign the app with a certificate and a mobile provisioning file, which is defined by a _label_ given by the `sign` attribute.

When creating a tarifa project, the [`create`](../usage/create.md) command will add signing and deploy informations
on the `stage`and the `prod` configuration and on the `signing` attribute in the `tarifa.json` and `private.json` files. Here is an example of the added attributes on the both files:

`tarifa.json`:

``` json
{
  "configurations": {
    "stage": {
      "release": true,
      "sign": "adhoc"
   },
    "prod": {
      "release": true,
      "sign": "store"
    }
  },
  "signing": {
    "ios": {
      "adhoc": {
        "provisioning_path": "/my/file2.mobileprovision",
        "provisioning_name": "xxxxx"
      },
      "store": {
        "provisioning_path": "/my/file.mobileprovision",
        "provisioning_name": "xxxxxxx"
      }
    }
  }
}
```

`private.json`:

```json
{
  "signing": {
    "ios": {
      "adhoc": {
        "identity": "xxxx"
      },
      "store": {
        "identity": "xxxxx"
      }
    }
  },
  "deploy": {
    "apple_id": "xxxxx",
    "apple_developer_team": "xxxxx"
  }
}
```

* `identity` is the apple developer identity
* `provisioning_path` is the path of the mobile provisioning file
* `provisioning_name` is the name of the mobile provision

See [`tarifa config`](../usage/config.md) to find commands to help you manage provisioning files and attached devices.

### Limitations

* [`tarifa run`](../usage/run.md) won't be able - like with other platforms - to automatically launch
the app on the device.
