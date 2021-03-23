
# JumpScript: openfd_check.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['node']
#### descr: 
```
Checks the number of open file descriptors for each process.
Result will be shown in the "System Load" section of the Grid Portal / Status Overview / Node Status page.

```
#### author: deboeckj@greenitglobe.com
#### period: 60
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/openfd_check.py
#### version: 1.0
#### timeout: 10
#### async: True
#### organization: greenitglobe
#### action_docstring: None
#### log: True