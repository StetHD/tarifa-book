# tarifa.json and private.json files

those two files are the description of a tarifa project and contains all needed
informations from configurations definitions to signing keys. `tarifa.json` is the
main description and `private.json` contains all not commitable stuff like apple ids or
path to keystore and so one.

Here is a `tarifa.json` example:

``` javascript
{
  "name": "myapp", // the default app name (can not be changed right now)
  "id": "org.tarifa.demo", // the default cordova app id (can not be changed right now)
  "description": "a simple app description", // project description
  "version": "1.0.0", // default version of app, it must have a 3 digits format
  "platforms": [
    "android",
    "web"
  ], // available platforms on project
  "plugins": [
    "org.apache.cordova.splashscreen"
  ], // cordova plugins
  "configurations": { // starting definitions of configurations:
    "android": {
      "default": {
        // we can overwrite the default values
        "id": "org.tarifa.demo",
        // the product name is the final name of the app, the one
        // you read on the store
        "product_name": "demo",
        // this is the name of the generated .apk file
        "product_file_name": "demo"
      },
      "dev": {
        "id": "org.tarifa.dev",
        "product_name": "demo dev",
        "product_file_name": "demo",
        // we can overwrite general attributes
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
        // we can add custom attributes for a given configuration
        "version_code": "1"
      }
    },
    "web": {
      "default": {
        "id": "org.tarifa.demo",
        "product_name": "demo",
        "product_file_name": "demo"
      }/* ,  ... */
    }
  },
  "cordova": { // default cordova settings
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

``` javascript
{
  "configurations": {
    "android": {
      "prod": {
        // information needed in order to sign the app in release mode
        // to deploy to store
        "keystore_path": "/path/to/my/key.keystore",
        "keystore_alias": "myalias"
      }
    }
  }
}
```
