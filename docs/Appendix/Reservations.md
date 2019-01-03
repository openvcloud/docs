# Reservations

Checking availability of sufficient amount of resources is essential prior to deploying CSs, VMs and virtual disks.
The resources like free disk space, CPUs, external IP addresses can be limited on account level as well as on CS level.
If CSs coexisting on the same account concurrently request resources, a race condition may occur leading to violation of the account limit.
To avoid race conditions all reservations should be scheduled on the account queue and executed sequentially.

The following actions schedule reservations on the account queue:

* [Create Cloudspace](Actions/CreateCS.md)
* [Create VM](Actions/CreateVM.md)
* [Create detach disk](Actions/CreateDetachedDisk.md)
* [Attach disk to VM](Actions/AttachDisk.md)