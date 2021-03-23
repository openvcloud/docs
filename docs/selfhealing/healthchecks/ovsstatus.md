
# JumpScript: ovsstatus.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['storagenode']
#### descr: 
```
Checks every predefined period (default 60 seconds) if all OVS processes are still running.
Result will be shown in the "OVS Services" section of the Grid Portal / Status Overview / Node Status page.
Shows WARNING if process is not running anymore.

```
#### author: khamisr@codescalers.com
#### period: 60
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/ovsstatus.py
#### version: 1.0
#### async: True
#### organization: cloudscalers
#### action_docstring: None
#### log: True