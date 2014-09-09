### the raw cordova app

The raw cordova app is located in the `app` folder, it remains a normal cordova app could be extracted from the project.

Right now, the tarifa build process still change settings in the cordova app without undoing them. This still need to be done.

On win32, the `www` project folder is copied to `app/www`, on other os, it's just a link.

For now tarifa just wrapps cordova plugins without any extra features.
