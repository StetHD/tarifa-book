# User settings

tarifa uses [configstore](https://www.npmjs.org/package/configstore) to store user settings.
User settings are used in [`tarifa create`](../usage/create.md) to prefill questions with default values,
for extending Cordova plugins list and www project templates list.

The `~/.config/configstore/tarifa.json` file has the following items:

#### User data

``` json
{
  "author_name": "my name",
  "author_email": "my@email",
  "author_href": "http://myblog"
}
```

#### Tokens, keystore and Apple ID

``` json
{
  "keystore_path": "/my/path/to/my/key.keystore",
  "hockeyapp_token": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
  "apple_id": "myappleid@oops.com",
  "apple_developer_team": "XXXXXXXXXX"
}
```

#### Cordova plugins

You can add some custom Cordova plugins, [`tarifa create`](../usage/create.md) will display them:

``` json
{
  "plugins": [
    {
      "name": "cordova-plugin-hockeyapp",
      "uri": "https://github.com/peutetre/cordova-plugin-hockeyapp.git",
      "value": "cordova-plugin-hockeyapp",
      "version": "0.1.0"
    }
  ]
}
```

[`tarifa update`](../usage/update.md) will also integrate them into the update process.

#### www project templates

You can also add custom www project templates, [`tarifa create`](../usage/create.md) will display them:

``` json
{
  "templates": [
    {
      "name": "browserify+stylus+preprocess",
      "value": "/Users/peutetre/code/test"
    },
    {
      "name": "react.js bootstrap",
      "value": "/Users/peutetre/code/react-bootstrap"
    }
  ]
}
```

#### Chrome path

On Linux or Windows, it's possible to set the Chrome path used in `tarifa run browser`:

``` json
{
  "chrome":"/usr/bin/chromium-browser"
}
```
