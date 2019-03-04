# Cloudsapce actions

## Disabling Cloudsapce

Active CSs in status DEPLOYED on enabled account can be disabled by calling action `disable` of cloudbroker:

* Prior to the action status of the Cloudsapce(CS) is set to DISABLING.
* Stop all VMs running on the CS.
* Stop VFW of the CS.
* If stopping any of VMs or stopping the VFW failed the CS is set back to status DEPLOYED.
* Ones all VMs and WFV stopped for the CS model set:
  * status to DISABLED;
  * flag `enabled` to `False`.

Actions allowed on disabled CSs (and all CS resources):

* for users of `admin` group: all actions allowed.
* for other users: no actions allowed.

## Enabling Cloudspace

Disabled CSs on enabled account can be enabled by calling action `enable`:

* Prior to the action status of the CS is set to ENABLING.
* Start VFW of the CS.
* If starting VFW failed, set CS status to PAUSED and proceed. Starting this VFW will be retried later by the health check `routeros_check.py`.
* Ones the VFW started (or set to PAUSED if failed starting) for the CS model set:
  * status to ENABLED;
  * flag `enabled` to `True`.
* Note that all VMs stay HALTED after enabling CS, user needs to start VMs.
