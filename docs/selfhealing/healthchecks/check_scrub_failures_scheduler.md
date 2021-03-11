
# JumpScript: check_scrub_failures_scheduler.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['master']
#### descr: 
```
Scheduler that runs on master that executes the check_scrub_failures to check scrub failures on the storage cluster.

```
#### author: kevin@gig.tech
#### period: 0 23 * * *
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/check_scrub_failures_scheduler.py
#### version: 1.0
#### timeout: 60
#### organization: greenitglobe
#### action_docstring: None