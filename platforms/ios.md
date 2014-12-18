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

On iOS, it is possible to deploy an app via ad-hoc distribution but this requires
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

See [`tarifa config`](../usage/config.md) to find commands to help you manage provisioning files and attached devices.

### Limitations

* [`tarifa run`](../usage/run.md) won't be able - like with other platforms - to automatically launch
the app on the device.
