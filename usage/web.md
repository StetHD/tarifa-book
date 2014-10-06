# web

The web is a `tarifa` platform like any other, except that it is way more simple.
Running

```
tarifa run web --verbose
```

in the project's root should open the `project/www/index.html` file in your browser
after building it with the default configuration and the node module defined in
`project/bin/build.js`.

In this platform the `tarifa build` command will only call `tarifa prepare`.

The configuration attributes are mandatory.
