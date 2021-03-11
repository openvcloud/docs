
# JumpScript: storage_check.py
        
#### category: monitor.healthcheck
#### enable: True
#### name: storage_check
#### descr: 
```
Checks the utilized capacity on the OVS backends and the objectspaces. 
Reports warning if any OSD or backend exceeds 80%  
Reports error if any OSD or backend exceeds 90%

```
#### author: mohamed.kasem@gig.tech
#### period: 600
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/storage_check.py
#### version: 1.0
#### roles: ['master']
#### timeout: 60
#### organization: jumpscale
#### action_docstring: None
#### log: True