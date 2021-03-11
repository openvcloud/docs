
# JumpScript: disk_scrub_schedule.py
        
#### category: monitor.maintenance
#### enable: True
#### roles: ['master']
#### descr: 
```
Scheduler that runs on master that executes the disk_scrub script to scrub disk with more storage than their specified size.

```
#### author: chaddada@greenitglobe.com
#### period: 0 22 * * *
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/maintenance/disk_scrub_schedule.py
#### version: 1.0
#### timeout: 60
#### organization: greenitglobe
#### action_docstring: None