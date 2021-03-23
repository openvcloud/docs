
# JumpScript: sshkey_check.py
        
#### category: monitor.maintenance
#### queue: process
#### enable: True
#### descr: 
```
This script checks if all the nodes have the sshkey from the other nodes authorized.

```
#### license: bsd
#### author: christophe@greenitglobe.com
#### period: 60
#### startatboot: True
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/maintenance/sshkey_check.py
#### version: 1.0
#### roles: ['cpunode', 'storagenode', 'storagedriver', 'controllernode']
#### async: True
#### organization: jumpscale
#### action_docstring: None
#### order: 1
#### log: False