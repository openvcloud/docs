
# JumpScript: cpu_physical_stats.py
        
#### category: monitoring.processes
#### enable: True
#### log: False
#### descr: 
```
Gathers following CPU statistics from physical machines:
- CPU time
- CPU percent
- Number of threads
- Number of context switches
- Number of interrupts

Statistics are writen to Redis.

```
#### author: kristof@incubaid.com
#### period: 60
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/collectors_stats/cpu_physical_stats.py
#### version: 1.0
#### roles: ['node']
#### organization: jumpscale
#### action_docstring: None