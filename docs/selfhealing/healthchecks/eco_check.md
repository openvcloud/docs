
# JumpScript: eco_check.py
        
#### category: monitor.healthcheck
#### enable: True
#### descr: 
```
Checks the number of error condidtions filed: if more than 5 are filed per hour will go into warning state,
and into error state if it exceeds 10 per hour

```
#### license: bsd
#### author: chaddada@greenitglobe.com
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/eco_check.py
#### version: 1.0
#### roles: ['master']
#### timeout: 20
#### async: True
#### organization: cloudscalers
#### action_docstring: None
#### log: True