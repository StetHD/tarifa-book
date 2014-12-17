# config

`tarifa config` gathers ios project configuration tasks and assets generation tasks.

The ios project configuration tasks allow to administrate provisioning files without visiting [http://developer.apple.com](http://developer.apple.com).

The assets generation part allows to create icons and splaschreens from a color or image file for a given configuration.

```
Usage: tarifa config <task>

Commands:

    ios devices list
        List all devices attached to the apple developer account

    ios devices list <configuration>
        List all devices attached to a given configuration
        by reading the mobile provisioning profile file

    ios devices add <name> <uuid>
        Add a device to the apple developer account

    ios devices attach <uuid> <configuration>
        Add a device to a configuration

    ios devices detach <uuid> <configuration>
        Remove a device from a configuration


    provisioning list
        List all available provisioning profiles on the current apple developer account


    icons generate <color> <configuration>
        Generate all icons with the given color in the given configuration

    icons file <path> <configuration>
        Generate all icons from given file in the given configuration

    splashscreens <color> <configuration>
        Generate all splash screens with the given color in the given configuration

Options:

    --help, -h     Show this message
    --verbose, -V  Be more verbose on everything

Examples:

    tarifa config ios devices list stage
```
