# info

`tarifa info` collects useful information about the current host, the current project and checks whether requirements are met. It will:

* check the Cordova install.
* check the required external tools.
* print version numbers of the Cordova platforms and required tools.
* print the ids of supported devices (`--verbose` to print human readable strings when available).
* print whether the command got called from inside a tarifa project.

```
Usage: tarifa info

Get some information about your environment and your devices.

Options:

    --help, -h            Show this message
    --verbose, -V         Be more verbose on everything
    --dump-configuration  Display the tarifa configuration after the parsing is done

Examples:

    tarifa info --verbose
```
