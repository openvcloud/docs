
# JumpScript: rabbitmq_partition_check.py
        
#### category: monitor.healthcheck
#### enable: True
#### roles: ['storagedriver']
#### descr: 
```
Check if there are partition issues in RabbitMQ. If issues were found it will restart RabbitMQ. 

```
#### author: jo@gig.tech
#### period: 900
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/rabbitmq_partition_check.py
#### version: 1.0
#### timeout: 180
#### organization: cloudscalers
#### action_docstring: None
#### log: True