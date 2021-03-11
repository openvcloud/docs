
# JumpScript: vm_disk_ratio_schedule.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['master']
#### descr: 
```
Scheduler that runs on master to check for disks/vms ratio
Generates warning if number of disks reached 6 times or more than number of machines.

```
#### author: foudaa@greenitglobe.com
#### period: 30 * * * *
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/vm_disk_ratio_schedule.py
#### version: 1.0
#### timeout: 60
#### organization: cloudscalers
#### action_docstring: None