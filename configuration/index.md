# Configuration

In tarifa, a configuration is a json object representing the settings of the app for a particular state of the project,
like for example the staging or the production states. Each configuration is described `tarifa.json` file on the root
of a tarifa project.

When creating a tarifa project with `tarifa create`, tarifa will create the following configurations: **_default_**, **_dev_**, **_stage_**, **_prod_**.
You can add or delete any configuration you like. The **_default_** configuration allows to call tarifa without specifying any name.

By default, the **_stage_** configuration is defined to be used for hockeyapp deployements (and ad-hoc distribution siging process on ios).

These configurations are just naming conventions, you can add any configurations you need and each configuration allows the build an unic app.
