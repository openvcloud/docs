
# JumpScript: deployment_test.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['cpunode']
#### descr: 
```
Tests every predefined period (default 30 minutes) whether test VM exists and if exists it tests write speed. Every 24hrs, test VM is recreated.
Result will be shown in the "Deployment Test" section of the Grid Portal / Status Overview / Node Status page.
Generates warning if write speed is lower than 50 MiB / second.

```
#### author: deboeckj@codescalers.com
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/deployment_test.py
#### version: 1.0
#### organization: cloudscalers
#### action_docstring: None
#### log: True