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

It's as simple as adding a `release_mode` attribute with the value `true`.
