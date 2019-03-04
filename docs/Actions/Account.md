# Account actions

## Disabling Account

Active account in status CONFIRMED can be disabled by calling administrative action `disable`:

* Prior to the action status of the account is set to DISABLING.
* Stop all Virtual Firewalls (VFWs) and all Virtual Machines (VMs) running on cloudspaces (CSs) of the account.
  * This action is only applied to enabled CSs, previously disabled CSs do not undergo any changes.
  * Stopping VFW for each CS results in changing CS's status PAUSED.
  * Stopping VM results in changing its status to HALTED.
* If pausing of any of CSs failed, account is set back to status CONFIRMED. Implication of this rollback action: all CSs that were set to PAUSED during the attempt of disabling account will be started again by the health check `routeros_check.py` .
* Ones all CSs are paused for the account model set:
  * status to DISABLED;
  * flag `enabled` to `False`.

Actions allowed on disabled accounts (and all account resources):

* for users of `admin` group: all actions allowed.
* for other users: no actions allowed.

## Enabling Account

Disabled accounts can be enabled by calling administrative action `enable`:

* Prior to the action status of the account is set to ENABLING
* Concurrently start CSs of the account:
  * Start only VFWs on CSs in status PAUSED, CSs in status DISABLED do not undergo any changes.
  * If error occurs when starting VFW, set CS status to PAUSED and proceed. Starting this VFW will be retried later by the health check `routeros_check.py`.
  * Note that all VMs stay HALTED after enabling Account, user needs to start VMs on his CSc.
* Ones all CSs are started for the account model set:
  * status to ENABLED;
  * flag `enabled` to `True`.

