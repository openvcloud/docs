## Jumpscripts and Jsagents

### Jumpscripts

A jumpscript is a python script with a specific convention that is supposed to do a specific and well defined task. They are basically modules that act like functions and executed whenever needed by getting queued either serially or in parallel, depending on the queue they get attached to. 



a typical jumscript looks something like this: 

```python
from JumpScale import j


descr = """
JUMPSCRIPT DESCRIPTION GOES HERE ....... 
"""

category = "<for example: cloudbroker>"
organization = "< for example: cloudscalers>"
author = "< for example: ali.chaddad@gig.tech>"
version = "< for example: 1.0 >"
roles = ["<for example: master>"]
queue = "< for example: hypervisor>"

# OTHER PARAMETERS 
log = True
enable = True
period = 3600
timeout = 900


def action():
    """Here you write the body of the function to be executed. This is specific to the jumpscript"""
    
    # There will almost always be some client being used. 
    # FOR EXAMPLE
    ccl = j.clients.osis.getNamespace("cloudbroker")


if __name__ == "__main__":
    action()

```

Jumpscripts are not necessarily simple, they could perform complex functions or extremely simple ones. It's also worth emphasizing that these scripts are almost never run manually, but instead are handled by an agent which is the [jsagent](#Jsagents)

Jumpscripts can be found in this [repo](https://git.gig.tech/openvcloud/openvcloud/-/tree/master/libs/agent-scripts) or in case you cloned the dev environment repository will be found at `/opt/code/git.gig.tech/openvcloud/openvcloud/libs/agent-scripts` 

The following guide explains the roles of the subfolders: 

**libvirt**:

contains the jumpscript used for setting up vms and vm actions

**demolitions**: 

currently not used

**jumpscripts**: 

contains subfolders with maintnenace stats collection and healtchecks

**resmonitoring**: 

billing collection
**vfw**: 

For managing the virtual routers



### Jsagents

These agents are services running on each node. They receive orders from a controller node in the cluster to perform some task. Upon receiving that order, the agent queues up a [jumpscript](#Jumpscripts) to be executed. The agents also append more meta information about the executed task along with the result of the jumscripts. 