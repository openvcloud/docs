
# JumpScript: arakoon_collapse_schedule.py
        
#### category: monitor.maintenance
#### enable: True
#### roles: ['master']
#### descr: 
```
Scheduler that runs on master that executes the arakoon_collapse.py

```
#### author: jo@gig.tech
#### period: 0 1 * * *
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/maintenance/arakoon_collapse_schedule.py
#### version: 1.0
#### timeout: 60
#### organization: greenitglobe
#### action_docstring: None