# Anatomy of a tarifa project

This is how a tarifa project looks like:

```
|-- app
|   |-- config.xml
|   |-- hooks
|   |-- merges
|   |-- platforms
|   |-- plugins
|   `-- www
|-- images
|-- project
|   |-- bin
|   |   |-- build.js
|   |   `-- mapping.json
|   |-- package.json
|   `-- www
|-- tarifa.json
`-- private.json
```

A tarifa project root is composed of 3 folders:

* `app` folder with the cordova app
* `images` folder containing all icons and splash screens
* `project` folder containing the www project

and 2 json files:

* `tarifa.json` containing the definition of the project and all configurations
* `private.json` containing all private informations (typically tokens, IDs,
  etc...) that you don't want to expose.

### the raw cordova app

The content of the `app` folder is a normal cordova application. Any cordova app
(version 3.4.x) should work with tarifa, thus you can use an existing cordova
app folder in a tarifa project.

At this time, the tarifa build performs settings replacement in various cordova
files without undoing them. In a future version of tarifa this won't be the case
anymore.

During the build process tarifa will copy or link the output of the `www` project
folder to `app/www`.

Currently, tarifa just wraps cordova plugins without any extra features.

### www project

It's a regular front-end project with the build system of your choice. It must
satisfy the following interface:

* having a `bin/build.js` node module exposing one function to launch the build
* generating output in a folder named `www`

The `bin/build.js` module must have the following signature:

``` javascript
var Q = require('q');

module.exports = function (platform, settings, configurationName) {
    // do async stuff then
    return Q.resolve();
}
```

 where

* `platform` is the platform chosen by the user
* `settings` is an object containing all project settings (resulting from the
merge of `tarifa.json` and `private.json`)
* `configurationName` is the configuration name chosen by the user for the current build

In the default tarifa project template, *browserify* is used in order to embed the configuration settings as
a global module named `settings` that you can require in your js code.

### `tarifa.json` and `private.json`

Those two files are the description of a tarifa project and contains all needed
informations from configurations definitions to keystore paths. `tarifa.json` is the
main description and `private.json` contains all private stuff like the Apple ID
or the hockeyapp token.

More in [Configurations](../configuration/index.md) chapter.
