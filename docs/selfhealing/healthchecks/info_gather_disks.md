
# JumpScript: info_gather_disks.py
        
#### category: monitor.healthcheck
#### enable: True
#### descr: 
```
Checks status of all physical disks and partitions on all nodes by checking free disk space on mount points
(except if / of mount point contains .dontreportusage - which is needed as an exception for read and write cache for OVS)

Throws WARNING per mount point if >90% used, throws ERROR per mount point if >95% used


```
#### license: bsd
#### author: zains@codescalers.com
#### period: 600
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/info_gather_disks.py
#### version: 1.0
#### roles: []
#### async: True
#### organization: jumpscale
#### action_docstring: None
#### log: True