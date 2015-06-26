# prepare

`tarifa prepare` is the first step of the [build chain](../workflow/indexhtml.md). It prepares the Cordova `www` folder by calling the [front-end project](../project/index.md#the-www-project) build `project/bin/build.js` with the given configuration and platform and then by symlinking/copying `project/www` to `app/www`.

```
Usage: tarifa prepare <platform> <configuration>

Build the output of the www project of your tarifa project.

Options:
    --help, -h     Show this message
    --verbose, -V  Be more verbose on everything
    --debug, -d    Print helpful stack trace on error

Examples:

    tarifa prepare prod android
```
