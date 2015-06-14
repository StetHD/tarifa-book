# Firefox OS

⚠ Current integration is experimental! ⚠

### Configuration attributes

In any Firefox OS configuration we need at least the following 3 attributes in the [`tarifa.json`](../project/index.md#tarifajson-and-privatejson) file :

``` json
{
  "id": "the.id.of.the.app",
  "product_name": "final app name",
  "product_file_name": "name_of_generated_zip_file"
}
```
Currently only the `product_name` and the `product_file_name` are used in the build process.


### Limitations

* works only on macosx
* `tarifa watch` is not supported
* the `manifest.webapp` generation is not ready for pushing apps to the marketplace

### Setting up development device

#### Remove user prompt on device while installing app

By default, the user gets prompted on the device twice while installing an app. It's possible to avoid this behavior by configuring b2g with the `prefs.js` user preference file on the device (firefoxos >= 2.0):


```sh
# get prefs.js remote path
export PREFJS=$(adb shell echo -n "/data/b2g/mozilla/*.default")/prefs.js
# fetch remote file
adb pull $PREFJS
```

then add:

```js
user_pref("devtools.debugger.forbid-certified-apps", false);
user_pref("devtools.debugger.prompt-connection", false);
user_pref("b2g.adb.timeout", 0);
```

to `prefs.js`. The next commands will upload the modified file and restart b2g.

```sh
adb push prefs.js $PREFJS
adb shell stop b2g
adb shell start b2g
```

#### Debug app with vorlonjs

To allow debugging app with vorlonjs, you need to add the following line in `prefs.js`:
```js
user_pref("security.apps.privileged.CSP.default", "default-src *; script-src *; object-src 'none'; style-src *");
```
It allows any remote scripts to be added in any packaged app, so **do this only on your development devices.**


