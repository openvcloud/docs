
# JumpScript: threads_check.py
        
#### category: monitor.healthcheck
#### enable: True
#### log: True
#### descr: 
```
Checks the number of threads, and throw an error if higher than expected.

Currently throws
- WARNING if more than 18K threads
- ERROR if more than 20K threads

Result will be shown in the "System Load" section of the Grid Portal / Status Overview / Node Status page.

```
#### author: christophe@greenitglobe.com
#### queue: process
#### scriptname: /opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts/jumpscripts/healthchecks/threads_check.py
#### version: 1.0
#### roles: ['node']
#### organization: jumpscale
#### action_docstring: None
#### order: 1