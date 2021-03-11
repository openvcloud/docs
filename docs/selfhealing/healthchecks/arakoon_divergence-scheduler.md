
# JumpScript: arakoon_divergence-scheduler.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['master']
#### descr: 
```
Scheduler that runs on master that executes the check_arakoon_divergence to check for arakoon divergence on the storage cluster.

```
#### author: kevin@gig.tech
#### period: 0 21 * * 3
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/arakoon_divergence-scheduler.py
#### version: 1.0
#### organization: greenitglobe
#### action_docstring: None