# User settings

tarifa use [configstore](https://www.npmjs.org/package/configstore) to get user settings.
User settings are used in `tarifa create` to prefill questions with default values
and for extending cordova plugins and www project templates lists.

`~/.config/configstore/tarifa.yml` can be edited and has the following items:

#### User data

``` yaml
author_name: my name
author_email: "my@email"
author_href: "http://myblog"
```

#### Tokens, keystore and apple id

``` yaml
keystore_path: /my/path/to/my/key.keystore
hockeyapp_token: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
apple_id: "myappleid@oops.com"
apple_developer_team: XXXXXXXXXX
```

#### cordova plugins

You can add some custom cordova plugins, `tarifa create` will show them:

``` yaml
plugins:
  - name: cordova-plugin-hockeyapp
    value: "https://github.com/peutetre/cordova-plugin-hockeyapp.git"
  - name: PhoneGap-ios-PhoneDialer
    value: "https://github.com/gaetansenn/PhoneGap-ios-PhoneDialer.git"
```

#### www project templates

You can also add custom www project templates, `tarifa create` will show them:

``` yaml
templates:
  - name: browserify+stylus+preprocess
    value: /Users/peutetre/code/test
  - name: react.js bootstrap
    value: /Users/peutetre/code/react-bootstrap
```
