# web

the web is a `tarifa` platform like anyother one, expect it's way more simple. Running

```
tarifa run web --verbose
```

in the root of the project should open the `project/www/index.html` in your browser after building it
with the default configuration and the node module provided in `project/bin/build.js`

In this platform the `tarifa build` will only call `tarifa prepare`.

Any configuration attributes are mandatory
