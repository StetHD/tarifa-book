# run

`tarifa run` executes the complete [build chain](../workflow/index.md). It prepares the `www` folder, builds the final app and runs it on any attached devices according to the given platform and configuration.

```
Usage: tarifa run <platform> [configuration]

Run the project on your device for the given platform, with no
configuration 'default' will be used.

Options:

    --help, -h     Show this message
    --verbose, -V  Be more verbose on everything

Examples:

    tarifa run android stage
```
