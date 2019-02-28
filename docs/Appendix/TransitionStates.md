# Transition states of OpenvCloud objects

Transition states are introduced for all OVC objects like **Machines**, **Cloudspaces**, **Accounts**, **Disks**, **Images** and **Nodes** to ensure that only one action is executed at a time. This is necessary to avoid race conditions caused by running actions simultaneously.

**Static** state is a state of an OVC object, which does not change unless requested or forced.
**Transition** state is a state of an OVC object that occurs while transitioning between static states. Each transition state represents an action that is being executed. One or several chained transitions can be necessary to reach from one static state to another.
Prior to running any action on an OVC object we ensure that transition from the current state to the target state is allowed.

## List of transition states of OVC objects

To all resources the following applies:

* DESTROYED - object is permanently deleted.
* DELETED - object moved to the recycle bin and will be permanently deleted after retention period.
* VIRTUAL or MODELED - only object model was created

### Virtual Machine states

|Initial State|Transition State| Desired State|
|---|---|---|
|VIRTUAL |DEPLOYING |RUNNING|
| RUNNING | PAUSING | PAUSED |
| PAUSED | RESUMING | RUNNING |
|RUNNING/PAUSED| STOPPING| HALTED |
|RUNNING/PAUSED| DELETING| DELETED |
|RUNNING/PAUSED| DESTROYING| DESTROYED  |
|HALTED| DELETING| DELETED |
|HALTED| DESTROYING| DESTROYED |


Actions restoring initial state:

|Initial State|Transition State|
|---|---|
|RUNNING <br> PAUSED <br> HALTED| REBOOTING <br> PAUSING <br>RESETTING <br> ADDING_DISK<br>ATTACHING_DISK <br>DETACHING_DISK <br> DELETING_DISK <br>  CREATING_TEMPLATE <br> CHANGING_DISK_LIMITS <br> CLONING <br> |

### Cloudspace states

|Initial State|Transition States| Desired State|
|---|---|---|
|VIRTUAL|DEPLOYING|DEPLOYED|
|DEPLOYED| DISABLING| DISABLED|
|DISABLED| ENABLING | DEPLOYED|
|DEPLOYED / DISABLED|DELETING|DELETED|
|DELETED| DESTROYING| DESTROYED|
|DELETED| RESTORING | DEPLOYED|
|DEPLOYED| PAUSING| PAUSED** |
|PAUSED*| RESUMING | DEPLOYED|
|DEPLOYED| RESETTING | DEPLOYED|

* State PAUSED indicates that the Virtual Firewall (VFW) was stopped. Self-healing is responsible to start the VFW and restore state DEPLOYED of the cloudspace.

### Account states

|Initial State|Transition States| Desired State|
|---|---|---|
|CONFIRMED| DISABLING | DISABLED|
|DISABLED| ENABLING | CONFIRMED|
|CONFIRMED / DISABLED| DESTROYING | DESTROYED |
|CONFIRMED / DISABLED| DELETING | DELETED |

### Disk states

|Initial State|Transition States| Desired State|
|---|---|---|
|MODELED|CREATING|CREATED|
|CREATED| ATTACHING | ASSIGNED|
|ASSIGNED| DETACHING | CREATED|
|CREATED| DELETING_DETACHED_DISK | DELETED |
|CREATED| DESTROYING | DESTROYED |
|ASSIGNED| DELETING_ATTACHED_DISK | TOBEDELETED |
|ASSIGNED| DESTROYING | DESTROYED |
|DELETED| RESTORING_ATTACHED_DISK | ASSIGNED |
|TOBEDELETED| RESTORING_DETACHED_DISK | CREATED |

* CREATED - detached disk.
* ASSIGNED - disk attached to a VM.
* DELETED - detached disk in recycle bin
* TOBEDELETED - attached disk in recycle bin (was deleted together with VM)

### Image states

|Initial State|Transition States| Desired State|
|---|---|---|
|VIRTUAL |CREATING|CREATED|
|CREATED | DISABLING| DISABLED|
|DISABLED|DISABLING|CREATED|
|CREATED / DISABLED| DELETING |  DELETED |
|CREATED / DISABLED| DESTROYING | DESTROYED |

### Node states

|Initial State|Transition States| Desired State|
|---|---|---|
|ENABLED| DEACTIVATING |MAINTENANCE|
|MAINTENANCE| ENABLING | ENABLED |
|ENABLED/MAINTENANCE| DECOMMISSIONING | DECOMMISSIONED|
|ENABLED | UPDATING | ENABLED |

## Rollback actions

If an action running on an OVC object fails, a 
Rollback action should be forseen for every action that can result in failure. Task of a rollback action is to revert changes and restore initial object state.
[objectqueue.py](../../apps/cloudbroker/cloudbrokerlib/objectqueue.py) module is used to handle flow of actions and rollbacks. Examples and explanation how to schedule actions and rollbacks using `ObjectQueue` class can be found [here](ObjectQueue.md).

Diagrams illustrating logic of rollback actions are [here](Actions/).

## Status handler

* Prior to scheduling an action on an OVC object, the status has to be changed to the corresponding transition state. Exception is automated migration of disks, machines and cloudspaces. In this case migration should be scheduled on the queue and executed after all previously added actions are executed.
* Change of states in db should only be done in unified way that guarantees **atomic state change**.

Validation of the transitions and status handling is implemented in module [`statushandler.py`](../../apps/cloudbroker/cloudbrokerlib/statushandler.py)

## Self-healing

It is important to have a self-healing script periodically running in order to repair states of the object stuck in transition states based on timeout.