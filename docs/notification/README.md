# Adding configuration to system-config.yaml
To enable sending notification for environment status change you need to add the following to system-config.yaml
```
alerting:
  key: <API_KEY>
  url: <API_URL>
```

# Adding configuration directly to the system config
In case you need to manipulate the system config manually for an existing environment without changing the config-map or in case on a local env setup
add the following configuration to this file `/opt/jumpscale7/cfg/system/system.yml`
```
alerting:
  key: <API_KEY>
  url: <API_URL>
```