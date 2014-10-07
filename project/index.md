# Anatomy of a tarifa project

This is what a tarifa project with ios and android platforms looks like:

<pre>
|-- app
|   |-- config.xml
|   |-- hooks
|   |-- platforms
|   |-- plugins
|   `-- www
|-- images
|   |-- android
|   `-- ios
|-- private.json
|-- project
|   |-- bin
|   |   |-- <b>build.js</b>
|   |   |-- <b>check_android.js</b>
|   |   |-- <b>check_ios.js</b>
|   |   |-- <b>check_web.js</b>
|   |   `-- <b>mapping.json</b>
|   |-- html
|   |   `-- <b>index.html</b>
|   |-- node_modules
|   |-- <b>package.json</b>
|   |-- src
|   |   `-- <b>app.js</b>
|   `-- www
`-- tarifa.json
<pre>

The root of a tarifa project is composed of 3 folders:

* `app` contains the cordova app.
* `images` contains all icons and splash screens.
* `project` contains the www project. (bold for editable files)

and 2 json files:

* `tarifa.json` defines the project and every single configuration.
* `private.json` consists of private data (typically tokens, IDs...) that you
don't want to expose.

### The raw cordova app

The `app` folder contains a regular cordova application. Any cordova app (version 3.6.x)
should work with tarifa, thus you can use an existing cordova app folder in a
tarifa project.

At this time, the tarifa build process performs setting replacements in various
cordova files without undoing them. In a future version of tarifa this won't be
the case anymore.

During the build process, tarifa will copy or link (depending on the OS) the output of the `www` project
folder to `app/www`.

Currently, tarifa just wraps cordova plugins without any extra features.

### The www project

The `project` folder is a regular front-end project with the build system of your choice. It must
satisfy the following interface:

* having a `bin/build.js` node module exposing a `build` function starting the build process.
* generating output in a folder named `www`.

More precisely, the `bin/build.js` module must have the following signature:

``` javascript
var Q = require('q');

module.exports.build = function (platform, settings, configurationName) {
    // do async stuff then
    return Q.resolve();
}
```

 where

* `platform` is the platform chosen by the user for the current build.
* `settings` is an object containing all the project settings (this object is
  simply the result of merging `tarifa.json` and `private.json`).
* `configurationName` is the name of the configuration chosen by the user (for
  instance `dev` or `prod` ).

In the default tarifa project template, *browserify* is used to embed the settings
which are specific to a configuration as a global module - named `settings` - that
you can require in your js code.

### `tarifa.json` and `private.json`

These two files wholly describe a tarifa project and contain everything that is
needed for building and managing it. This goes from the definition of the various
configurations to the keystore paths. `tarifa.json` defines most of the data and
`private.json` contains all the private stuff, such as the Apple ID or the hockeyapp
token, that you don't want to share publicly.

A more detailed description may be found in the [Configurations](../configurations/index.md)
chapter.
