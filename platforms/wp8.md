# Windows Phone 8

### Configuration attributes

The `wp8` configuration requires at least the following 4 attributes in the [`tarifa.json`](../project/index.md#tarifajson-and-privatejson) file:

``` json
{
  "id": "the.javapackage.name",
  "product_name": "final app name",
  "product_file_name": "name_of_generated_apk_file",
  "guid": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX"
}
```

* `id` is the C# namespace of the application.
* `product_name` is the final app name which is shown on your device's OS.
* `product_file_name` is the name of the compiled .xap file.
* `guid` is the guid of the application, needed to uniquely identify the app
(tarifa create will generate some for you) and hence to be able to run multiple
variations of it.
* `release` set the release mode, `false` by default.
* `sign` is the signing label.
* `hockeyapp_id` is the id of the app on kockeyapp.

### Signing attributes

To deploy to HockeyApp, WP8 apps need to be signed with a certificate in PFX format and you need an application enrollment token (AET).
See [http://msdn.microsoft.com/en-us/library/windows/apps/jj206943.aspx](http://msdn.microsoft.com/en-us/library/windows/apps/jj206943.aspx) for more informations.

To sign the build of a configuration for Company app distribution,
you need to set the configuration attributes `certificate_path` with the path of the certificate in the _signing label_ and `release` to true.
