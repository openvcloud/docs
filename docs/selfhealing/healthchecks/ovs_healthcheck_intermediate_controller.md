
# JumpScript: ovs_healthcheck_intermediate_controller.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['master']
#### descr: 
```
Calls the standard Open vStorage health checks, see: https://github.com/openvstorage/openvstorage-health-check
Result will be shown in the "OpenvStorage" section of the Grid Portal / Status Overview / Node Status page.

```
#### author: foudaa@codescalers.com
#### period: 600
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/ovs_healthcheck_intermediate_controller.py
#### version: 1.0
#### timeout: 590
#### organization: cloudscalers
#### action_docstring: None
#### log: True