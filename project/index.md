### Anatomy of a tarifa project

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

You can spot the cordova project in the `app` folder. The `images` folder is the
collection of icons and splashscreens needed for the project. The `project` folder
is the `www` folder project builder (you can see it just as a very common front-end project).
The `tarifa.json` and `private.json` files are the definition of the project.
