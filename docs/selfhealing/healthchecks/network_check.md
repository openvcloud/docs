
# JumpScript: network_check.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['controllernode', 'cpunode', 'storagenode']
#### descr: 
```
Check that nodes are in the expected networks with correct IPS and mac addresses

```
#### author: ali.chaddad@gig.tech
#### period: 3600
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/network_check.py
#### version: 1.0
#### timeout: 60
#### organization: greenitglobe
#### action_docstring: None
#### log: True