
# JumpScript: selfhealing_threashold.py
        
#### category: monitor.maintenance
#### NETS_REDIS_KEY: throttle.net.%s
#### enable: True
#### descr: 
```
Finds all logs on known logs files and executes logs truncate

```
#### license: bsd
#### author: muhamada@greenitglobe.com
#### IOPS_REDIS_KEY: throttle.iops.%s
#### period: 60
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/maintenance/selfhealing_threashold.py
#### version: 1.0
#### roles: ['statscollector']
#### NETS_THRESHOLD: 1
#### async: True
#### organization: 0-complexity
#### action_docstring: None
#### NETS_PACKET_THRRSHOLD: 500
#### IOPS_THRESHOLD: 200
#### log: True