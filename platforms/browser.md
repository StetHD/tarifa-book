# browser

### Configuration attributes

In any browser configuration we need at least the following 3 attributes in the [`tarifa.json`](../project/index.md#tarifajson-and-privatejson) file:

``` json
{
  "id": "com.example",
  "product_name": "final app name",
  "product_file_name": "final_app_name"
}
```

* `id` some reverse domain name.
* `product_name` the final app name, which you may choose to display on your web app using *settings*.
* `product_file_name` some name that won't be used (see the note just below).

These three keys are not that useful for the browser platform, but you must assign them values
otherwise tarifa won't let you build & run the project for that platform.
