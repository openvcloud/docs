
# JumpScript: volumedriver_update_schedule.py
        
#### category: monitor.maintenance
#### enable: True
#### roles: ['controller']
#### descr: 
```
Scheduler that runs on controller that executes the volumedriver_update script to update disks edge ip and port in case its storagedriver is changed.

```
#### period: 3600
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/maintenance/volumedriver_update_schedule.py
#### version: 1.0
#### timeout: 3600
#### async: True
#### organization: greenitglobe
#### action_docstring: None