
# JumpScript: vdisk_checker.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['master']
#### descr: 
```
check 'destroyqueuetimestamp' of disks in 'TOBEDESTROYED' status and create an error if it is there for more than 7days and warning if it is there for more than 2days

```
#### author: ashraf.fouda@gig.tech
#### startup: True
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/vdisk_checker.py
#### version: 1.0
#### organization: greenitglobe
#### action_docstring: None
#### log: True