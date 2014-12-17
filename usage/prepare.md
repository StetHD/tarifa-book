# prepare

`tarifa prepare` is the first step of the [build chain](../workflow/indexhtml.md). It prepares the cordova `www` folder by calling the [front-end project](../project/index.md#the-www-project) build `project/bin/build.js` with the given configuration and platform then symlinking/copying `project/www` to `app/www`.

```
Usage: tarifa prepare <platform> [configuration]

Build the output of the www project of your tarifa project, with no
configuration 'default' will be used.

Options:
    --help, -h     Show this message
    --verbose, -V  Be more verbose on everything

Examples:

    tarifa prepare android prod
```
