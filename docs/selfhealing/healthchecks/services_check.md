
# JumpScript: services_check.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['controllernode', 'cpunode', 'storagenode']
#### descr: 
```
Check that all openvcloud/openvstorage services are up and running on the nodes.

```
#### author: ali.chaddad@gig.tech
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/services_check.py
#### version: 1.0
#### timeout: 120
#### organization: cloudscalers
#### action_docstring: None
#### log: True