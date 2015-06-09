# User settings

<b style="background:yellow">TODO</b>
<b style="background:yellow">no more yaml file -> now, it's a json file since configstore@1.0.0</b>

tarifa uses [configstore](https://www.npmjs.org/package/configstore) to get user settings.
User settings are used in [`tarifa create`](../usage/create.md) to prefill questions with default values,
for extending Cordova plugins list and www project templates list.

The `~/.config/configstore/tarifa.yml` file has the following items:

#### User data

``` yaml
author_name: my name
author_email: "my@email"
author_href: "http://myblog"
```

#### Tokens, keystore and Apple ID

``` yaml
keystore_path: /my/path/to/my/key.keystore
hockeyapp_token: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
apple_id: "myappleid@oops.com"
apple_developer_team: XXXXXXXXXX
```

#### Cordova plugins

You can add some custom Cordova plugins, [`tarifa create`](../usage/create.md) will display them:

``` yaml
plugins:
  - name: cordova-plugin-hockeyapp
    uri: "https://github.com/peutetre/cordova-plugin-hockeyapp.git"
    value: com.zengularity.cordova.hockeyapp
    version: 0.0.0
  - name: PhoneGap-ios-PhoneDialer
    value: com.phonegap.core.phonedialer
    uri: "https://github.com/gaetansenn/PhoneGap-ios-PhoneDialer.git"
    version: 0.2.0
```

[`tarifa update`](../usage/update.md) will also integrate them into the update process.

#### www project templates

You can also add custom www project templates, [`tarifa create`](../usage/create.md) will display them:

``` yaml
templates:
  - name: browserify+stylus+preprocess
    value: /Users/peutetre/code/test
  - name: react.js bootstrap
    value: /Users/peutetre/code/react-bootstrap
```

#### Chrome path

On Linux or Windows, it's possible to set the Chrome path used in `tarifa run browser`:

``` yaml
chrome:/usr/bin/chromium-browser
```
