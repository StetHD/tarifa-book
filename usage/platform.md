# platform

`tarifa platform` wrapps `cordova platform` and edit [`tarifa.json`](../project/index.md#tarifajson-and-privatejson) according to the sub command.

```
Usage: tarifa platform <cmd> [platform]

Add, remove or list cordova platforms in your project.

Available commands:

    add <platform>
        Add a new platform of type <platform>
    remove <platform>
        Remove the platform of type <platform>
    list
        List installed platforms

Options:

    --help, -h     Show this message
    --verbose, -V  Be more verbose on everything

Examples:

    tarifa platform add ios
```
