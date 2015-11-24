# Working with push notifications

`tarifa` supports the push notification plugin `phonegap-plugin-push` as a default cordova plugin and provides
a few extras to copy icons and sounds. Only iOS and Android are currently supported.

While creating a tarifa project with `tarifa create`, if `phonegap-plugin-push` is choosen, tarifa will copy the default extra notifications icons needed for Android.

Extra icons and sounds are specified for a specific configuration like:

```
images/
├── android
│   └── default
│       ├── icons
│       │   └── ...
│       ├── images              // extra icon `notif`
│       │   ├── notif-144.png
│       │   ├── notif-192.png
│       │   ├── notif-36.png
│       │   ├── notif-48.png
│       │   ├── notif-72.png
│       │   └── notif-96.png
│       ├── sounds              // extra sounds
│       │   └── ...
│       └── splashscreens
│           └── ...
└── ios
    └── default
        ├── icons
        │   └── ...
        ├── sounds              // extra sounds
        │   └── ...
        └── splashscreens
            └── ...
```

Refer to the plugin official [documentation](https://github.com/phonegap/phonegap-plugin-push/blob/master/README.md) for more informations on how to use.

### Extra sounds

On iOS and Android, it's possible to add custom sounds for notifications. Sounds are located in the project folders `images/<configuration>/android/sounds` and `images/<configuration>/ios/sounds`.

On iOS you need to convert your input file to the proper format (see [ios push documentation](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/IPhoneOSClientImp.html#//apple_ref/doc/uid/TP40008194-CH103-SW6) for more informations):

```
afconvert -f caff -d LEI16 {INPUT} {OUTPUT}
```

### Extra icons

On Android, it's possible to add custom icons. They are defined in `images/<configuration>/android/images` of a tarifa project. Create a project with `phonegap-plugin-push` to get the default notifications icons.

### Working example

This [example](https://github.com/peutetre/broadcast) is a "Simple broadcast" working on Android and iOS platforms with custom sounds and notifications icons.
