
# JumpScript: cpu_ctxpy_check.py
        
#### category: monitor.healthcheck
#### enable: True
#### log: True
#### descr: 
```
Checks the number of CPU context switches per second. If higher than expected an error condition is thrown.

Currently throws:
- WARNING if more than 1M context switches/s
- ERROR if more than 600k context switches/s

Result will be shown in the "System Load" section of the Grid Portal / Status Overview / Node Status page.

TODO : check these values, specifically if amount of cores per CPU is growing

```
#### author: deboeckj@codescalers.com
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/cpu_ctxpy_check.py
#### version: 1.0
#### roles: ['node']
#### organization: jumpscale
#### action_docstring: None
#### order: 1