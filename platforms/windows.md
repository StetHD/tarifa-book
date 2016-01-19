# Windows

### Configuration attributes

The `windows` configuration requires at least the following 4 attributes in the [`tarifa.json`](../project/index.md#tarifajson-and-privatejson) file:

``` json
{
  "id": "my.namespace",
  "product_name": "final app name",
  "product_file_name": "name_of_generated_universal_app",
  "guid": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX"
}
```

* `guid` is the guid of the application, needed to uniquely identify the app
(tarifa create will generate some for you) and hence to be able to run multiple variants of it.
* `release` toggles the release mode, `false` by default.
* `hockeyapp_id` is the id of the app on kockeyapp.
