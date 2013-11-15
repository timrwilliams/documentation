# Custom Config Add-on

The custom config Add-on allows you to add custom credentials to the standard
creds.json file provided for each of your deployments. This allows you to keep
code in branches and additional configuration settings needed for the
deployment seperated from each other.

An example for such a configuration, could be the Amazon S3 credentials. You
would probably want to use different ones for production and development and
the Custom Config Add-on allows you to do this.

## Adding Configuration Settings

To add configuration settings simply invoke the config command with the add
option and append the desired `key`, `value` pairs.
~~~bash
$ cctrlapp APP_NAME/DEP_NAME config.add KEY=VALUE
~~~

This will automatically add the Config Add-on to your deployment.

Replace APP_NAME, DEP_NAME, KEY and VALUE with the desired values and they will
be added to your deployment's cred.json file.

To set multiple settings at once simply append more than one key/value pairs.
~~~bash
$ cctrlapp APP_NAME/DEP_NAME config.add KEY1=VALUE1 KEY2=VALUE2 [...]
~~~

Config parameters can be set as in the following table and the are stored in
JSON format. Multiline arguments can be set using the `\n` escape character.

CLI parameter|JSON representation
---|--- 
key=value|{"key": "value"}
key="multiline\nvalue"|{"key": "multiline\nvalue"}
key|{"key": true}

Note: It is recommended to use double quotes `"` for setting multispace or
multiline values to make sure they are stored properly.

## Listing Configuration Settings

You can list the existing set of configuration settings by invoking the config
command:
~~~bash
$ cctrlapp APP_NAME/DEP_NAME config
KEY1=VALUE2
KEY2=VALUE1
~~~

To show the value of a specific key simply append the desired key name:
~~~bash
$ cctrlapp APP_NAME/DEP_NAME config KEY
KEY=VALUE
~~~

## Updating Configuration Settings

To add or remove settings to your custom config simply use the `add` or
`remove` option of the config command and append the parameters you need.
~~~bash
$ cctrlapp APP_NAME/DEP_NAME config.add [-f|--force] NEW_PARAM=NEW_VALUE [...]
$ cctrlapp APP_NAME/DEP_NAME config.remove PARAM1 PARAM2 [...]
~~~

Updating the existing settings is also possible, using the `add` command. This
will require your confirmation unless you use the `-f` or `--force` flag after
the add command.

## Removing the Config Addon

Deleting all the existing configuration from a deployment can be done by
removing the Add-on.
~~~bash
$ cctrlapp APP_NAME/DEP_NAME addon.remove config.free
~~~

This will remove all the custom configuration settings.

