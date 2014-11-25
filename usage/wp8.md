# Windows Phone 8


### Configuration attributes

The `wp8` configuration requires at least the following 4 attributes in the `tarifa.json`
file:

``` json
{
  "id": "the.javapackage.name",
  "product_name": "final app name",
  "product_file_name": "name_of_generated_apk_file",
  "guid": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX"
}
```

* `id` is the C# namespace of the application.
* `product_name` is the final app name which is shown on your devices' OS.
* `product_file_name` is the name of the compiled .xap file.
* `guid` is the guid of the application, needed to uniquely identify the app
(tarifa create will generate some for you) and hence to be able to run multiple
variations of it.

### Release

Add `release_mode` attribute with the value `true` to your release configuration.

### Deploy with hockeyapp

To deploy to hockeyapp, wp8 apps need to be signed and you need an application enrollment token (AET).
See [http://msdn.microsoft.com/en-us/library/windows/apps/jj206943(v=vs.105).aspx](http://msdn.microsoft.com/en-us/library/windows/apps/jj206943(v=vs.105).aspx)
to create an AET file. To sign the build of a configuration for Company app distribution,
you need to set the `sign_mode` and `release_mode` attributes to true.
