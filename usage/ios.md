# iOS

### Configuration attributes

In any ios configuation we need at least those 3 attributes in the `tarifa.json` file:

``` json
{
  "id": "the.bundle.id",
  "product_name": "final app name",
  "product_file_name": "name_of_generated_ipa_file"
}
```

* `id` is the bundleid of the application.
* `product_name` is the final app name, the one you read on the screen
* `product_file_name` is the name of the compiled .ipa file

On iOS, it's possible to deploy an app via ad-hoc distribution which needs to sign
the app with a certificat and a mobile provisioning file. When creating a tarifa project,
the `create` command will add signing and deploy information on the stage configuration in the `private.json` file.

``` json
{
  "stage": {
    "hockeyapp_id": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
    "apple_developer_identity": "iPhone Distribution: XXXXXXXX (XXXXXXXXXX)",
    "provisioning_profile_path": "./test.mobileprovision",
    "provisioning_profile_name": "atestname"
  }
}
```

### Limitations

* `tarifa run` will not be able to launch the app on the device, like other devices.
