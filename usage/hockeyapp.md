# hockeyapp

`tarifa hockeyapp` allows to interact with [http://hockeyapp.net](hockeyapp.net) for publishing apps to testers.

General hockeyapp configuration goes under the `hockeyapp` key:

``` json
{
  "hockeyapp": {
    "api_url": "https://rink.hockeyapp.net/api/2",
    "token": "a2b9b0d16ca8407dac61539af21e88f7"
  }
}
```

This is the minimal configuration to be able to interact with hockeyapp. Of course we suggest to use `private.json` to store sensitive data like hockeyapp token.

The command `version upload` will perform differenlty depending on what you have in your configuration.

If you already have created an application on hockeyapp, then add the `hockeyapp_id` key for the configuration setting you want in your `tarifa.json`. The command will upload the last built package to a new version of your hockeyapp application, using this id.

If you don't have created an application on hockeyapp, the command `version upload` will create it for you, upload the last built package and append the `hockeyapp_id` in your `tarifa.json`.


```
Usage: tarifa hockeyapp <command>

Commands:

    version list <platform> <config>
        Fetch the list of hockeyapp versions of <config> env for given platform.

    version upload <platform> <config> [options]
        Upload a version of <config> env package to hockeyapp for given platform.
        Options can be any of 'notes', 'notify', 'status', 'tags', 'teams', 'users',
        'commit_sha', 'build_server_url', 'repository_url'.
        See http://support.hockeyapp.net/kb/api/api-versions#upload-version for details.

    version update <platform> <config> [options]
        Modify last version of given platform for <config> env. You can only
        modify metadatas; you can't upload a new package.
        Options can be any of 'notes', 'notify', 'status', 'tags', 'teams', 'users',
        'commit_sha', 'build_server_url', 'repository_url'.
        See http://support.hockeyapp.net/kb/api/api-versions#update-version for details.

    version clean <keep>
        Clean all versions of all apps found in tarifa.json; specify the number
        of versions to keep (default: 3).

Options:

    --help, -h     Show this message
    --verbose, -V  Be more verbose on everything
```
