
# JumpScript: sshkey_check.py
        
#### category: monitor.maintenance
#### queue: process
#### enable: True
#### log: False
#### descr: 
```
This script checks if all the nodes have the sshkey from the other nodes authorized.

```
#### author: jo.de.boeck@gig.tech
#### period: 60
#### startatboot: True
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/maintenance/sshkey_check.py
#### version: 1.0
#### roles: ['cpunode', 'storagenode', 'storagedriver', 'controllernode']
#### organization: jumpscale
#### action_docstring: None
#### order: 1