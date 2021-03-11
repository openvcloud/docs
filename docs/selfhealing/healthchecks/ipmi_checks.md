
# JumpScript: ipmi_checks.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['cpunode', 'storagenode']
#### descr: 
```
Checks the power redundancy of a node using IPMItool.
Result will be shown in the "Hardware" section of the Grid Portal / Status Overview / Node Status page.

```
#### author: geert.audenaert@gig.tech
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/ipmi_checks.py
#### version: 1.0
#### timeout: 30
#### organization: cloudscalers
#### action_docstring: None
#### log: True