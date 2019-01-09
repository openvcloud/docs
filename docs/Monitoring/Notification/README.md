# Healtcheck Notifications

It is possible to configure a callback url to post events when the system health status changes.
This requires two configuration keys (see below how to configure) the url where to post to and optionally an api key.

## Post Request

Whenever a change in the status of the system happens, the system will do a post to the configured url:
```
POST <configured url>
Authorization: Bearer <configured api key>

{"env": "<fqdn of environment>"}
```


## Adding configuration to system-config.yaml
To enable sending notification for environment status change you need to add the following to system-config.yaml
```
alerting:
  key: <API_KEY>
  url: <API_URL>
```

[Write System Config](../../Installation/Installer-script#cluster-resources-writeconfig)

## Adding configuration directly to the system config
In case you need to manipulate the system config manually for an existing environment without changing the config-map or in case of a local env setup
add the following configuration to this file `/opt/jumpscale7/cfg/system/system.yml`
```
alerting:
  key: <API_KEY>
  url: <API_URL>
```
