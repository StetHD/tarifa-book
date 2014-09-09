### wwww project

It's a regular front-end project with the build system you want with the following interface:

* have a `bin/build.js` node module exposing a function to launch the www build process
* generate output in a `www` folder

The `bin/build.js` node will be used by tarifa during the build process and have the
following signature:

``` javascript
var Q = require('q');

module.exports.build = function (platform, settings, configurationName) {
    // do async stuff then
    return Q.resolve();
}
```

`platform` is the platform choosen by the user
`settings` is a object containing all project settings
`configurationName` is the configuration name choosen by the user for the current build
