
# JumpScript: volumedriver_check.py
        
#### category: monitor.healthcheck
#### queue: process
#### enable: True
#### log: True
#### descr: 
```
healthcheck that monitors rouge volumedriver  by checking its threads count and memory consumptio

```
#### author: muhamada@greenitglobe.com
#### VOLUMEDRIVER_NAME: volumedriver_fs
#### MEMORY_THRESHOLD: 0.4
#### period: 300
#### THREAD_THRESHOLD: 2000
#### startatboot: True
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/volumedriver_check.py
#### version: 1.0
#### roles: ['storagedriver']
#### timeout: 250
#### organization: jumpscale
#### action_docstring: None
#### order: 1