# Requests limits

To prevent attacks such as DDOS there is a limit of possible requests that can be sent from a user.
This restriction is implemented on three levels:

## System wide

This limit is done on the nginx server that limits the number of requests allowed per ip address.
This limit should be generous enough to not disturb the user's activity and is there as a protection of the web server.
Stricter limitation are placed in the other levels.

## Per User

The portal server enforces a limit per the user account. If the limit is exceeded it will send a too many requests response and the user has to wait a certain period before sending requests again.

This works by storing each request in redis with the username + timestamp as key with expiration as speified in the config.
If the number stored at the same time exceeds the allowed limit, no more requests are allowed as long as the limit is still reached.

## Per IP

This is the same as above but with a much lower allowance used for unregistered users(guests).

### Configuring the limits

The limits configuration comes from the system config they are under `environment.settings.requests_limits`.
If not specified the default settings at `j.core.default_config.DEFAULT_REQUESTS_LIMITS` are used.

#### Overview of the config

```json
{"guest": {"requests_count": 10, "requests_expiry": 5},
 "user": {"requests_count": 20, "requests_expiry": 5},
 "server": 10}
```

- `requests_count`: Number of allowed stored requests per user
- `requests_expiry`: The expiry of each stored request, in sec
- `server`: The rate of allowed requests per sec
