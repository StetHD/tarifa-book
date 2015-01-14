# check

`tarifa check` needs to be executed after cloning a tarifa project. It will:
* initialize the Android platform, if available.
* check each iOS provisioning files, if available.
* initialize your [front-end project](../project/index.md#the-www-project) — by calling `npm install` in the `project` folder.
* execute every [user script](../configurations/index.md#check) defined in [`tarifa.json`](../project/index.md#tarifajson-and-privatejson) scripts.

```
Usage: tarifa check

Check the current working project after cloning

Options:

    --help, -h     Show this message
    --verbose, -V  Be more verbose on everything
```
