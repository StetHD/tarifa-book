# platform

`tarifa platform` wraps `cordova platform` and edits the [`tarifa.json`](../project/index.md#tarifajson-and-privatejson) file. All supported cordova platforms are listed by `tarifa platform info`. If no version mentioned in `tarifa platform add`, the last supported version is installed.

```
Usage: tarifa platform <cmd> [platform]

Add, remove or list cordova platforms in your project.

Available commands:

    add <platform|platform@version>
        Add a new platform of type <platform>
    remove <platform>
        Remove the platform of type <platform>
    list
        List installed platforms
    info
        List supported cordova platforms

Options:

    --help, -h     Show this message
    --verbose, -V  Be more verbose on everything

Examples:

    tarifa platform add ios
```
