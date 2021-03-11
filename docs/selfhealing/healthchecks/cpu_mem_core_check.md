
# JumpScript: cpu_mem_core_check.py
        
#### category: monitor.healthcheck
#### enable: True
#### log: True
#### descr: 
```
Checks average memory and CPU usage/load. If average per hour is higher than expected an error condition is thrown.

For both memory and CPU usage throws WARNING if more than 80% used and throws ERROR if more than 95% used.

Result will be shown in the "System Load" section of the Grid Portal / Status Overview / Node Status page.

```
#### author: deboeckj@codescalers.com
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/cpu_mem_core_check.py
#### version: 1.0
#### roles: ['node']
#### organization: jumpscale
#### action_docstring: None
#### order: 1