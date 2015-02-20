# check

`tarifa check` needs to be executed after cloning a tarifa project. It will:
* regenerate the cordova app according to the [`tarifa.json`](../project/index.md#tarifajson-and-privatejson) file if no `app` folder found in the root of the projet.
* initialize the Android platform, if available.
* check each iOS provisioning files, if available.
* initialize your [front-end project](../project/index.md#the-www-project) — by calling `npm install` in the `project` folder.
* execute every [user script](../configurations/index.md#check) defined in [`tarifa.json`](../project/index.md#tarifajson-and-privatejson) scripts.

```
Check the current working project after cloning and regenerate the cordova app if not found.

Options:

    --help, -h     Show this message
    --force        Force cordova app regenerate
    --verbose, -V  Be more verbose on everything
```
