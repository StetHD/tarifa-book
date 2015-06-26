# run

`tarifa run` executes the complete [build chain](../workflow/index.md). It prepares the `www` folder, builds the final app and runs it on any attached devices according to the given platform and configuration.

```
Usage: tarifa run <platform> [configuration]

Run the project on your device for the given platform. You can either
specify names or wildcards.

Options:

    --help, -h              Show this message
    --verbose, -V           Be more verbose on everything
    --all                   Run on all available devices
    --nobuild               Skip build process if build available
    --log, -l               Output app debug logs, only for single build
    --vorlon, -D            Debug app with vorlon.js
    --arch <ARCH>           Android only: choose your device architecture. Can
                            be either 'armv7' or 'x86'. It is mainly useful when
                            developing with the crosswalk-webview-plugin.
                            If you're using crosswalk, tarifa will assume 'armv7'
                            as default arch, so this flag is optional.
    --debug, -d             Print helpful stack trace on error

Examples:

    tarifa run android           # will run default conf for android platform
    tarifa run android dev       # will run dev conf for android platform
    tarifa run all dev           # will run dev conf for all platforms
    tarifa run ios dev,stage     # will run dev and stage confs for ios
    tarifa run ios,android dev   # will run dev conf for ios and android platforms
    tarifa run all all           # will run all confs for all platforms
```

### debug

With the `--vorlon` option, `tarifa run` will spawn `vorlonjs` server. You need to add the `vorlon` script in your main `index.html` file (default `project/www/index.html`):

```html
<script src="http://yourhost:1337/vorlon.js"></script>
```
