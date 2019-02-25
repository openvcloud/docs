# Selfhealing for objects stuck in transition

Potentially OVC objects can be stuck in transition states:

1. due to the node shutdown, lead to all tasks to be interrupted
2. due to a bug, that has to be reported and fixed

Self-healing script for transition states should recover such objects from transition states to the appropriate static states.

## Account

* DISABLING: set property ENABLED to True -> set status to CONFIRMED -> attempt disabling account
* ENABLING: set property ENABLED to False -> set status to CONFIRMED -> attempt enabling account
* DELETING: set status to CONFIRMED -> attempt deleting account
* RESTORING: set status to DELETED -> attempt restoring account
* DESTROYING: set account status to DESTROYED, set statuses of all CSs, machines and images to DESTROYED, set status of all disks to TOBEDESTROYED (rely of a self-healing script to clean up objects)
* UPDATING: set to status CONFIRMED

## Cloudspace

* DEPLOYING: set status to DESTROYED
* DESTROYING: set status to DESTROYED (rely of a self-healing script to clean up machines that survived destroying CS)
* DISABLING: set property ENABLED to True -> attempt disabling CS
* ENABLING: set property ENABLED to False -> attempt enabling CS
* DELETING: 
    * if disabled CS: set status to DEPLOYED -> attempt deleting CS
    * if enabled CS: set status to PAUSED -> attempt deleting CS  
* UPDATING: set to status DEPLOYED
    * if disabled CS: set status to DEPLOYED -> attempt deleting CS
    * if enabled CS: set status to PAUSED -> attempt deleting CS
* RESTORING: set status to DELETED -> attempt restoring CS
* PAUSING: set status to PAUSED -> call cloudspace.get() api to refresh CS status.

## Machine

* DEPLOYING: set status to DESTROYED
* DESTROYING: set status to DESTROYED (rely of a self-healing script to clean up machines that survived destroying)
* STOPPING, STARTING, REBOOTING, RESETTING, ADDING_DISK, ATTACHING_DISK, DETACHING_DISK, DELETING_DISK, CHANGING_DISK_LIMITS, CLONING, RESIZING, CREATING_TEMPLATE, RESTORING:
    * set VM status to HALTED -> call `api.machines.get()` in order to update real status of the VM to HALTED or RUNNING
* DELETING -> set status to HALTED, set disk statuses to ASSIGNED -> attempt deleting machine
* RESTORING -> set status to DELETED, set disk statuses to TOBEDELETED -> attempt deleting machine

## Disk

* DELETING_ATTACHED_DISK, DESTROYING_ATTACHED_DISK, RESTORING_ATTACHED_DISK: ignore, should be handled together with VM
* DELETING_DETACHED_DISK: set status to DELETED
* RESTORING_ATTACHED_DISK: set status to CREATED
* DETACHING/ATTACHING/RESIZING:
    * if listed on any machines -> set status to ASSIGNED
    * otherwise -> set status to CREATED

## Image

* CREATING: set status to DESTROYED (rely of a self-healing script to clean up images that survived destroying)
* RESTORING -> set status to DELETED -> attempt restoring image
* DELETING: set status to CREATED -> attempt deleting image
* DESTROYING: set status to DESTROYED (rely of a self-healing script to clean up images that survived destroying)

## Node and Stack

All checks and status updates perform for node and corresponding stack object at the same time.

* DEACTIVATING: set status to ENABLED -> attempt putting node in maintenance
* ENABLED: set status to MAINTENANCE -> attempt enabling node
* DECOMMISSIONING: set status to ENABLED -> attempt decommissioning