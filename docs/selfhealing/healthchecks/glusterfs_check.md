
# JumpScript: glusterfs_check.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['controllernode']
#### descr: 
```
Checks that glusterfs server is running on the controller node and that each node in the cluster can see the other nodes.
The script also checks for the consumed storage and report based on the state.

```
#### author: ali.chaddad@gig.tech
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/glusterfs_check.py
#### version: 1.0
#### timeout: 30
#### organization: greenitglobe
#### action_docstring: None
#### log: True