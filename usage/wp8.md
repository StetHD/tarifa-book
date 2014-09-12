# Windows Phone 8


### Configuration attributes

The `wp8` configuration needs at least those 4 following attributes in the `tarifa.json` file:

``` json
{
  "id": "the.javapackage.name",
  "product_name": "final app name",
  "product_file_name": "name_of_generated_apk_file",
  "guid": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX"
}
```

* `id` is the C# namespace of the application.
* `product_name` is the final app name, the one you read on the screen
* `product_file_name` is the name of the compiled .xap file
* `guid` is the guid of the application, this is needed for the uniqueness of the app (tarifa create will generate some for you)

### Release

it's simple as adding a `release_mode` attribute with the value `true`.
