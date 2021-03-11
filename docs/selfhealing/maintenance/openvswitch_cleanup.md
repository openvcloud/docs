
# JumpScript: openvswitch_cleanup.py
        
#### category: monitor.maintenance
#### enable: True
#### roles: ['cpunode']
#### descr: 
```
Cleans bridge interfaces that are in error state

```
#### author: ashraf.fouda@gig.tech
#### startup: True
#### period: 0 0 * * *
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/maintenance/openvswitch_cleanup.py
#### version: 1.0
#### timeout: 60
#### organization: greenitglobe
#### action_docstring: None
#### log: True