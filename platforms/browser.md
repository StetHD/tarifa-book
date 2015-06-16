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

### Execution

Running

```
tarifa run browser --verbose
```

in a tarifa project should open the `app/platforms/browser/www/index.html` file in your Chrome browser
after building it with the default configuration and the build process defined in the [front-end project](../project/index.md#the-www-project) build system module `project/bin/build.js`.

### Limitations

`tarifa run browser` may fail if the Chrome executable is not found. Defining the path of your Chrome executable
in `~/.config/configstore/tarifa.json` should fix it (See [user settings](../settings/index.md) for defining the Chrome path).

`tarifa watch browser` fails to open Chrome pointing to the right url.
