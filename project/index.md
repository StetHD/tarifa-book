# Anatomy of a tarifa project

This is what a tarifa project looks like for iOS and Android — using the default project template (**bold for editable files**):

<pre>
|-- <b>tarifa.json</b>                     /* project definition */
|-- <b>private.json</b>                    /* private project definition */
|-- app                             /* contains the cordova app */
|   |-- config.xml
|   |-- hooks
|   |-- platforms
|   |-- plugins
|   `-- www                         /* link/copy from `project/www` */
|-- images                          /* icons + splashscreens */
|   |-- android
|   `-- ios
`-- project                         /* front-end project */
    |-- bin
    |   |-- <b>build.js</b>                /* front-end project's build interface to tarifa */
    |   |-- <b>check_android.js</b>        /* custom user scripts ran by `tarifa check` */
    |   |-- <b>check_ios.js</b>
    |-- node_modules
    |   `-- ...
    |-- <b>package.json</b>
    |-- src
    |   `-- <b>app.js</b>
    |-- test
        `-- <b>test.js</b> /* end to end tests */
    `-- www                         /* front-end project's output linked/copied to cordova's www */
        |-- <b>style.css</b>
        `-- <b>index.html</b>
</pre>

The root of a tarifa project is composed of 3 folders:

* `app` contains the cordova app.
* `images` contains all icons and splash screens.
* `project` contains the www project.

and 2 json files:

* `tarifa.json` defines the project and every single configuration.
* `private.json` consists of private data (typically tokens, IDs...) that you
don't want to expose.

### The raw Cordova app

The `app` folder contains a regular Cordova application. Any Cordova app (version 4.x.x)
should work with tarifa, thus you can use an existing Cordova app folder in a
tarifa project.

At this time, the tarifa build process performs setting replacements in various
Cordova files without undoing them. In a future version of tarifa this won't be
the case anymore.

During the build process and before finishing the [prepare step](../usage/prepare.md), tarifa will copy or link (depending on the OS) the output of the `www` project folder to `app/www`.

The `app` folder can be regenerated with [`tarifa check --force`](../usage/check.md) command.

### The www project

The `project` folder is a regular front-end project with the build system of your choice. It must
satisfy the following interface:

* having a `package.json`.
* having a `bin/build.js` node module exposing the `build`, `watch`, `close` and `test` functions that respectively start the build process, start the live reload, stop it and launch end to end tests.
* generating output in a folder named `www` or if defined, at the path given by the `project_output` attribute in `tarifa.json`.

More precisely, the `bin/build.js` module must have the following signature:

``` javascript
var Q = require('q');

module.exports.build = function (platform, settings, config) {
    // do async stuff then
    return Q.resolve();
}

module.exports.watch = function watch(f, settings, platform, config, confEmitter) {
    // init front-end watch
    // then call `f(<changed file path>)`
    // each time the live reload needs to be triggered

    // you may also listen to the `change` event emitted by `confEmitter`
    // to receive the configuration object for the specified `platform`
    // and `config` when it is updated in the `tarifa.json` file
}

module.exports.close = function close() {
    // close all watch handlers used in `watch()`
    // called by tarifa on ^C
}

module.exports.test = function (platform, settings, config, caps, appium, verbose) {
    // launch tests then
    return Q.resolve();
};

```

where

* `platform` is the platform chosen by the user for the current build.
* `settings` is an object containing all the project settings (this object is
  simply the result of merging `tarifa.json` and `private.json`).
* `config` is the name of the configuration chosen by the user.
* `f` is a function which shall be called each time a file needs to be reloaded. It takes the path of the changed file as an argument.
* `caps` is an object representing the appium server capabilities needed to launch the tests
* `appium` is an object describing the appium server configuration:
``` js
{ host: 'localhost', port: 4723 }
```
* `verbose` is a boolean representing the `--verbose` option

In the default tarifa project template, [browserify](http://browserify.org/) is used to embed the settings
which are specific to a configuration as a global module — named `settings` — that you can require in your js code.

See the [default template www project build script](https://github.com/TarifaTools/tarifa/blob/master/template/project/bin/build.js) for a complete example.

### `tarifa.json` and `private.json`

These two files wholly describe a tarifa project and contain everything that is
needed for building and managing it. This goes from the definition of the various
configurations to the keystore paths. `tarifa.json` defines most of the data and
`private.json` contains all the private stuff, such as the Apple ID or the HockeyApp
token, that you don't want to share publicly.

A more detailed description can be found in the [Configurations](../configurations/index.md)
chapter.
