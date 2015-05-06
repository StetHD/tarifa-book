# watch

`tarifa watch` wraps `tarifa run` to instantly update your app with code and configuration changes.

The [front-end project](../project/index.md#the-www-project) build script needs to expose the functions `watch()` and `close()`. An example is provided in the default template using [watchify](https://www.npmjs.com/package/watchify) and [chokidar](https://www.npmjs.com/package/chokidar) (refer to [build.js](https://github.com/TarifaTools/tarifa/blob/master/template/project/bin/build.js)). tarifa is only watching the `tarifa.json` file, watching source code in the front-end project is left to user space through the `watch()` function.

The default port which serves the app is `7042`. The live reload server uses a self assigned port between `35729` and `35829`.

```
Usage: tarifa watch <platform> [configuration]

Watch the current project on the given platform, with no
configuration 'default' will be used.

Options:

    --port=PORT, -p=PORT  Set http server port, default is 7042
    --norun               Skip install and run app steps
    --help, -h            Show this message
    --verbose, -V         Be more verbose on everything
```
