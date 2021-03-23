
# JumpScript: disk_orphan_schedule.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['controller']
#### descr: 
```
Scheduler that runs on controller to check for orphan disks on specific volume driver nodes.
Generates warning if orphan disks exist on the specified volumes.

```
#### author: deboeckj@codescalers.com
#### period: 30 3 * * *
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/disk_orphan_schedule.py
#### version: 1.0
#### timeout: 3600
#### async: True
#### organization: cloudscalers
#### action_docstring: None