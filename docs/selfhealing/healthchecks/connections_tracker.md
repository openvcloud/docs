
# JumpScript: connections_tracker.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['cpunode', 'storagenode', 'controllernode']
#### descr: 
```
Monitors if connections exceeded 80% of allowed connections
Problems are reported in the "Network" section of the Grid Portal / Status Overview / Node Status page.

```
#### author: ashraf.fouda@gig.tech
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/connections_tracker.py
#### version: 1.0
#### timeout: 60
#### organization: cloudscalers
#### action_docstring: None
#### log: True