# Updating an existing project

When you create a tarifa project with the `tarifa create` command a hidden `.tarifa.json` file is written to the project's root. That file holds a JSON object composed of two attributes: the `created` attribute stores the version of tarifa used on project creation and the `current` attribute stores the version of tarifa used upon the latest execution of the `tarifa update` command.

Here is an example `.tarifa.json` file, which reflects a project created with tarifa **v0.2.5** and updated to **v0.3.0**:
```json
{
  "current": "0.3.0",
  "created": "0.2.5"
}
```

Right now, when you execute the `tarifa update` command in an existing tarifa project:

1. Each installed platform and plugin gets updated to the latest available version.
2. The `.tarifa.json` file is overwritten with an updated `current` attribute.

Note that the various tarifa files are not automatically updated, but we provide detailed instructions in tarifa's `CHANGES.md` file.
