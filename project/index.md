# Anatomy of a tarifa project

A tarifa project `example` looks like that:

```
example
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

A tarifa project is composed of 3 folders:

* `app` folder with the cordova app
* `images` folder containing all icons and splashscreens
* `project` folder containing the www project

and 2 json files:

* `tarifa.json` containing a commitable definition of the project
* `private.json` containing all private informations needed to deploy or sign the apps.

### the raw cordova app

The content of the `app` folder is a normal cordova app that should be extractable from the project.
Right now, the tarifa build process still change settings in the cordova app without undoing them. This still need to be done.

During the build process tarifa will copy or link the output of  the `www` project folder to `app/www`.

Right now tarifa just wrapps cordova plugins without any extra features.

### www project

It's a regular front-end project with the build system you want satisfying the following interface:

* have a `bin/build.js` node module exposing a function launching the build process
* generate output in a folder name `www`

The `bin/build.js` module have the following signature:

``` javascript
var Q = require('q');

module.exports = function (platform, settings, configurationName) {
    // do async stuff then
    return Q.resolve();
}
```

 where

* `platform` is the platform choosen by the user
* `settings` is a object containing all project settings (merged `tarifa.json` and `private.json` objects)
* `configurationName` is the configuration name choosen by the user for the current build

In the default tarifa project template, browserify is used in order to embed the configuration settings as
a global module named `settings` that you can require in your js code.

### `tarifa.json` and `private.json`

Those two files are the description of a tarifa project and contains all needed
informations from configurations definitions to keystore paths. `tarifa.json` is the
main description and `private.json` contains all not commitable stuff like apple id or hockeyapp token.

See more in [Configurations](configuration/index.md) chapter.

