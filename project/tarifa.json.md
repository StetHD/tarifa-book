# tarifa.json and private.json files

those two files are the description of a tarifa project and contains all needed
informations from configurations definitions to signing keys. `tarifa.json` is the
main description and `private.json` contains all not commitable stuff like apple ids or
path to keystore and so one.

Here is a `tarifa.json` example:

``` json
{
  "name": "myapp",
  "id": "org.tarifa.demo",
  "description": "a simple app description",
  "version": "1.0.0",
  "platforms": [
    "android",
    "web"
  ],
  "plugins": [
    "org.apache.cordova.splashscreen"
  ],
  "configurations": {
    "android": {
      "default": {
        "id": "org.tarifa.demo",
        "product_name": "demo",
        "product_file_name": "demo"
      },
      "dev": {
        "id": "org.tarifa.dev",
        "product_name": "demo dev",
        "product_file_name": "demo",
        "version": "2222.0.0"
      },
      "stage": {
        "id": "org.tarifa.stage",
        "product_name": "demo stage",
        "product_file_name": "demo",
        "version": "123.0.0"
      },
      "prod": {
        "id": "org.tarifa.demo",
        "product_name": "demo prod",
        "product_file_name": "demo",
        "version_code": "1"
      }
    },
    ...
  },
  "cordova": {
    "preferences": {
      "DisallowOverscroll": true,
      "EnableViewportScale": false,
      "KeyboardDisplayRequiresUserAction": false,
      "ShowSplashScreenSpinner": false,
      "HideKeyboardFormAccessoryBar": false,
      "SplashScreen": "screen",
      "AutoHideSplashScreen": true,
      "KeyboardShrinksView": true,
      "KeepRunning": true
    },
    "accessOrigin": [
      "*"
    ]
  },
  "author": {
    "name": "your name",
    "email": "me@tarifa.tools",
    "href": "http://tarifa.tools"
  }
}
```

and the according `private.json` file:

``` json
{
  "configurations": {
    "android": {
      "prod": {
        "keystore_path": "/path/to/my/key.keystore",
        "keystore_alias": "myalias"
      }
    }
  }
}
```
