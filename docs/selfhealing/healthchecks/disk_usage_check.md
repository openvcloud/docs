
# JumpScript: disk_usage_check.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['node']
#### descr: 
```
Checks status of all physical disks and partitions on all nodes, reporting back the free disk space on mount points.

(except if / of mount point contains .dontreportusage - which is needed as an exception for read and write cache for OVS)

Throws WARNING per mount point if >90% used, throws ERROR per mount point if >95% used.

```
#### author: zains@codescalers.com
#### period: 60
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/disk_usage_check.py
#### version: 1.0
#### timeout: 20
#### organization: jumpscale
#### action_docstring: None
#### log: True