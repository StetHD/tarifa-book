# build

`tarifa build` executes the whole [build chain](../workflow/index.md) except the `run` step. It prepares the `www` folder by calling `project/bin/build.js` (refer to [the front-end project](../project/index.md#the-www-project)) and builds the final app according to the given platform and configuration.

```
Usage: tarifa build <platform> [configuration]

Build the project for the given platform, with no
configuration 'default' will be used.

Options:

    --help, -h              Show this message
    --verbose, -V           Be more verbose on everything
    --keep-file-changes     Keep all modifications made by tarifa in your files

Examples:

    tarifa build android prod
```
