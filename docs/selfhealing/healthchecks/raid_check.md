
# JumpScript: raid_check.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['node']
#### descr: 
```
Checks whether all configured RAID devices are still healthy.
Result will be shown in the "Hardware" section of the Grid Portal / Status Overview / Node Status page.

```
#### author: deboeckj@greenitglobe.com
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/raid_check.py
#### version: 1.0
#### timeout: 60
#### async: True
#### organization: cloudscalers
#### action_docstring: None
#### log: True