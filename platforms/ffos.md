# Firefox OS

⚠ Current integration is experimental! ⚠

### Configuration attributes

In any Firefox OS configuration we need at least the following 3 attributes in the [`tarifa.json`](../project/index.md#tarifajson-and-privatejson) file :

``` json
{
  "id": "the.id.of.the.app",
  "product_name": "final app name",
  "product_file_name": "name_of_generated_zip_file"
}
```
Currently only the `product_name` and the `product_file_name` are used in the build process.


### Limitations

* works only on macosx machines
* `tarifa watch` is not supported
* the `manifest.webapp` generation is not ready for pushing apps to the marketplace
