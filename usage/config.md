# config

`tarifa config` gathers iOS project configuration tasks and assets generation tasks.

The iOS project configuration tasks allow you to administrate provisioning files without visiting [http://developer.apple.com](http://developer.apple.com).

The assets generation tasks allow you to create icons and splaschreens from a color or image file for a given configuration.

```
Usage: tarifa config <task>

Options:

    --help, -h     Show this message
    --verbose, -V  Be more verbose on everything
    --debug, -d    Print helpful stack trace on error

Commands:

    icons generate <color> <configuration>
        Generate all icons with the given color in the given configuration

    icons file <path> <configuration>
        Generate all icons from given file in the given configuration

        Options:
            --bgColor=<color>   replace alpha channel with <color> on iOS icons

    splashscreens <color> <configuration>
        Generate all splash screens with the given color in the given configuration


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

    provisioning info <configuration>
        Extract informations from the provisioning profile file linked in the given configuration

    provisioning fetch
        Answer questions to fetch provisioning file from apple.com
```
