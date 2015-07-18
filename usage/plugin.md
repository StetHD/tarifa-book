# plugin

`tarifa plugin` wraps `cordova plugin` and edits the [`tarifa.json`](../project/index.md#tarifajson-and-privatejson) file to keep track of
installed plugins and their configuration like id, version, uri or variables as described in [`tarifa.json`'s plugin description](../configurations/index.md#plugins).

```
Usage: tarifa plugin <cmd>

Add, remove or list cordova plugins in your project.

Available commands:

    add <plugin>
        Add a new plugin identified by <plugin>
    install <plugin>
        Alias add command
    remove <plugin>
        Remove the plugin
    reload <plugin>
        Reinstall the plugin
    list
        List installed plugins

Options:

    --variable     Only for `add` command, defines variable
                   to be passed to the cordova plugin on install
    --link         symlink android files for development
    --help, -h     Show this message
    --verbose, -V  Be more verbose on everything
    --debug, -d    Print helpful stack trace on error

Examples:

    tarifa plugin add https://github.com/peutetre/cordova-plugin-hockeyapp.git#0.0.0
    tarifa plugin add org.apache.cordova.vibration
    tarifa plugin add ./relative/path/to/a/cordova/plugin
    tarifa plugin add ./relative/path/to/a/cordova/plugin-with-variables --variable MY_VAR1=oops --variable MY_VAR42=42
    tarifa plugin add ./relative/path/to/a/cordova/plugin --link
```
