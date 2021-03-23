
# JumpScript: nodestatus.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['cpunode', 'storagenode']
#### descr: 
```
Checks the status of each node.

ERROR state is automatically attributed to a node by OpenvCloud - this is done if a specific action cannot be executed anymore on the Node.

Result will be shown in the "Node Status" section of the Grid Portal / Status Overview / Node Status page.

```
#### author: deboeckj@codescalers.com
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/nodestatus.py
#### version: 1.0
#### async: True
#### organization: cloudscalers
#### action_docstring: None
#### log: True