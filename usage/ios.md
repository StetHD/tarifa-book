# iOS

### Configuration attributes

In any ios configuration we need at least these 3 attributes in the `tarifa.json`
file:

``` json
{
  "id": "the.bundle.id",
  "product_name": "final app name",
  "product_file_name": "name_of_generated_ipa_file"
}
```

* `id` the bundleid of the application.
* `product_name` the final app name which is shown on your devices's OS.
* `product_file_name` the name of the compiled .ipa file.

On iOS, it's possible to deploy an app via ad-hoc distribution but this requires
the app to be signed with a certificate and a mobile provisioning file. When
creating a tarifa project, the `create` command will add signing and deploy information
on the stage configuration in the `private.json` file.

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
