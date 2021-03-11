
# JumpScript: db_check.py
        
#### category: monitor.healthcheck
#### enable: True
#### name: info_gather_db
#### descr: 
```
Checks status of MongoDB database on Master. If not running an error condition is thrown.
Result will be shown in the "Databases" section of the Grid Portal / Status Overview / Node Status page.

```
#### author: zains@codescalers.com
#### period: 600
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/db_check.py
#### version: 1.0
#### roles: ['master']
#### timeout: 60
#### organization: jumpscale
#### action_docstring: None
#### log: True