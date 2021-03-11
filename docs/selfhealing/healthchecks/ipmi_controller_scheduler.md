
# JumpScript: ipmi_controller_scheduler.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['master']
#### descr: 
```
Runs the ipmi check on the controller nodes.
Since the controllers share the same hardware, if the check succeeds on one node, the failed check won't be reported.

```
#### author: ali.chaddad@gig.tech
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/ipmi_controller_scheduler.py
#### version: 1.0
#### timeout: 600
#### organization: cloudscalers
#### action_docstring: None