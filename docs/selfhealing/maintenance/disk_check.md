
# JumpScript: disk_check.py
        
#### category: monitor
#### enable: True
#### roles: ['storagedriver']
#### descr: 
```
Checks for orphan disks create model for them if it doesn't exist and set its status to 'TOBEDESTROYED' to be picked up by the disks_destroyer script

```
#### author: ashraf.fouda@gig.tech
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/maintenance/disk_check.py
#### version: 1.0
#### timeout: 3500
#### organization: greenitglobe
#### action_docstring: None
#### log: True