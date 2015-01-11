# build

`tarifa build` executes the whole [build chain](../workflow/index.md) except the `run` step. It prepares the `www` folder by calling `project/bin/build.js` (refer to [the front-end project](../project/index.md#the-www-project)) and builds the final app according to the given platform and configuration.

```
Usage: tarifa build <platform> [configuration]

Build the project for the given platforms and configurations. You can either
specify names or wildcards.

Options:

    --help, -h              Show this message
    --verbose, -V           Be more verbose on everything
    --keep-file-changes     Keep all modifications made by tarifa in your files
    --clean-resources       Clean cached resources (icons and splashscreens) before build,
                            only for android platform

Examples:

    tarifa build android           # will build default conf for android platform
    tarifa build android dev       # will build dev conf for android platform
    tarifa build all dev           # will build dev conf for all platforms
    tarifa build ios dev,stage     # will build dev and stage confs for ios
    tarifa build ios,android dev   # will build dev conf for ios and android platforms
    tarifa build all all           # will build all confs for all platforms

```
