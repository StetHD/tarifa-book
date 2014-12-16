# build

`tarifa build` executes all the [build chain](../workflow/index.md) except the `run` step: prepares the `www` folder and build the final app according to the given platform and configuration.

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
