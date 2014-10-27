# browser

### Configuration attributes

In any browser configuration we need at least the following 3 attributes in the `tarifa.json`
file:

``` json
{
  "id": "com.example",
  "product_name": "final app name",
  "product_file_name": "final_app_name"
}
```

* `id` some reverse domain name.
* `product_name` the final app name, which you may choose to display on your web app using *settings*.
* `product_file_name` some name that won't be use (see the note below).

These three keys are not that useful for the browser platform, but you must assign them values
otherwise tarifa won't let you build & run the project for that platform.

### Execution

Running

```
tarifa run browser --verbose
```

in the project's root should open the `project/www/index.html` file in your browser
after building it with the default configuration and the node module defined in
`project/bin/build.js`.
