
# JumpScript: disk_physical_stats.py
        
#### category: disk.monitoring
#### enable: True
#### log: False
#### descr: 
```
Gathers following statistics about the physical disks:
- time_read
- time_write
- count_read
- count_write
- kbytes_read
- kbytes_write
- MB_read
- MB_write
- space_free_mb
- space_used_mb
- space_percent

```
#### author: kristof@incubaid.com
#### period: 60
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/collectors_stats/disk_physical_stats.py
#### version: 1.0
#### roles: ['node']
#### organization: jumpscale
#### action_docstring: None
#### order: 1