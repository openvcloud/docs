
# JumpScript: ovs_disk_safety.py
        
#### category: disk.monitoring
#### enable: True
#### descr: 
```
Gathers statistics about disk safety and sends this disk safety statistics for each vpool and the amount of namespaces with the lowest disk safety to the database.

```
#### license: bsd
#### author: christophe@greenitglobe.com
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/collectors_stats/ovs_disk_safety.py
#### version: 1.0
#### roles: ['storagemaster']
#### timeout: 60
#### async: True
#### organization: greenitglobe
#### action_docstring: Send disk safety for each vpool and the amount of namespaces with the lowest disk safety to DB
#### order: 1
#### log: False