# Deletion of Cloudspaces

Call to delete a CS can be received via API from the user's side or from admin portal.
In order to delete a CS with API call, no VMs in non-deleted states should be present in the CS. If such VMs are present in the CS, request will return error.
Unlike sending API call, deleting Cloudbroker via portal is an admin action and allows deleting CS together with its VMs. First all VMs are scheduled for deleting and then the CS itself.

## Deleting to Recycle Bin

If parameter `permanently` is set to `False`, CS will be moved to the Recycle Bin, where it can be restored from during the [retention period](link to Recbin Doc page).
Expected outcome of the action: stopped VFW, CS status is set to DELETED

If VFW failed to stop, CS status has to be set to the initial status.

## Deleting permanently

CS's deleted with flag `permanently` cannot be restored. Prior to deleting CS, all VMs in status DELETED have to be destroyed permanently.
Next step after VM's are cleaned up and CS's can be safely deleted, is to release resources occupied by the CS:

* delete VFW
* release Private Network
* release External IP address

If deletion of VFW fails, we proceed anyway to releasing other resources and setting CS to status DESTROYED.
VFW will be cleaned up by the health check assigned to delete firewalls that are no longer a part of an active CS.

![](https://docs.google.com/drawings/d/e/2PACX-1vRbP-YbXJnR2i2TXBaTLo6RaAyMsfUxhh3tJek4TxsJVEjR770--w-DZn82A5MHnBtVlCMOXWgBFqfw/pub?w=2395&h=1355)