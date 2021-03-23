
# JumpScript: vm_network_load.py
        
#### category: monitor.healthcheck
#### enable: True
#### log: True
#### descr: 
```
Checks the bandwith consumption of the network utilized by the virtual machine
> 8k packets WARNING
> 10k packets  ERROR

```
#### author: deboeckj@greenitglobe.com
#### period: 180
#### queue: process
#### WARNING_TRESHHOLD: 8000
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/vm_network_load.py
#### roles: ['cpunode']
#### timeout: 60
#### async: True
#### organization: cloudscalers
#### action_docstring: None
#### order: 1
#### ERROR_TRESHHOLD: 10000