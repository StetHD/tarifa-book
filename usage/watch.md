# watch

`tarifa watch` wrapps `tarifa run` and features live reload.

The [front-end project](../project/index.md#the-www-project) build script needs to expose the functions `watch()` and `close()`. The default template provides an example with [watchify](https://www.npmjs.com/package/watchify) and [chokidar](https://www.npmjs.com/package/chokidar).

The default port which serves the app is `7042`. The livereload server use a self assigned port between `35729` and `35829`.

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
