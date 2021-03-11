
# JumpScript: alba_maintenance_restart.py
        
#### category: monitor.maintenance
#### enable: True
#### log: True
#### descr: 
```
This script restarts alba maintenance to prevent a known bug from occuring which causes the process to hang.
It restarts each service once a day.

```
#### author: ali.chaddad@gig.tech
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/maintenance/alba_maintenance_restart.py
#### version: 1.0
#### roles: ['storagenode', 'cpunode']
#### organization: greenitglobe
#### action_docstring: None