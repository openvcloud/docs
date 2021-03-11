
# JumpScript: swap_used_check.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['node']
#### descr: 
```
Checks the amount of swap used by the system, and throws an error if higher than expected.

Currently throws:
- WARNING if more than 10 GB
- ERROR if more than 14 GB

Result will be shown in the "System Load" section of the Grid Portal / Status Overview / Node Status page.

```
#### author: christophe@greenitglobe.com
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/swap_used_check.py
#### version: 1.0
#### organization: jumpscale
#### action_docstring: None
#### order: 1
#### log: True