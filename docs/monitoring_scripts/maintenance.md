## maintenance

### Name: alba_maintenance_restart
#### Description

This script restarts alba maintenance to prevent a known bug from occuring which causes the process to hang.
It restarts each service once a day.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|storagenode, cpunode|monitor.maintenance|

### Name: alba_proxy_restart
#### Description

This script alba proxy restart command every days at 7 in the morning .

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|storagenode|monitor.maintenance|

### Name: arakoon_collapse
#### Description

This script collapses arakoon on a daily basis

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A||monitor.maintenance|

### Name: arakoon_collapse_schedule
#### Description

Scheduler that runs on master that executes the arakoon_collapse.py

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|0 1 * * *|60|master|monitor.maintenance|

### Name: arakoon_upgrade_restart
#### Description


#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|storagenode|maintenance|

### Name: asd_check
#### Description

This script checks that the asd services are running if not it attempts to fix by healing the devicename

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|120|cpunode, storagenode, storagedriver|monitor.maintenance|

### Name: asd_heal
#### Description

This script updates the device name of an asd disk.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A||monitor.maintenance|

### Name: balance
#### Description

This script executes btrfs balance command every 5 days at 4 in the morning random .

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|60|cpunode, storagenode, storagedriver|monitor.maintenance|

### Name: change_proxies_to_cache_on_read
#### Description

This script will set all proxies to cache on read.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A||upgrade|

### Name: clean_obsoleted_versions
#### Description

Clean obsoleted images versions if it is not used

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|3600|120|storagedriver|monitor.maintenance|

### Name: cloudspace_deployment_state
#### Description

Redeploy cloudspaces that are in status virtual

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|master|monitor.healthcheck|

### Name: dbmaintenance
#### Description

Cleanup old databases

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|25 2 * * *|1800|master|maintenance|

### Name: dhcp_orphan
#### Description

Checks orphan dhcps on the node.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|3600|N/A|cpunode|monitor.maintenance|

### Name: disk_check
#### Description

Checks for orphan disks create model for them if it doesn't exist and set its status to 'TOBEDESTROYED' to be picked up by the disks_destroyer script

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|3500|storagedriver|monitor|

### Name: disk_check_schedule
#### Description

Scheduler that runs on master to check on disk status.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|21600|3600|master|monitor.maintenance|

### Name: disk_devicename
#### Description

This script self heal the device name of disks after a boot of the system.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|storagedriver|monitor.maintenance|

### Name: disk_garbage_collector
#### Description

Checks for stale metadata disks on volume driver nodes.
Inspired by http://pastebin.com/CghxtDHp from Jeffrey Devloo (OVS) <- This link might expire...

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|storagedriver|selfhealing|

### Name: disk_garbage_collector_schedule
#### Description

Scheduler that runs on master to check for orphan disks on specific volume driver nodes.
Generates warning if orphan disks exist on the specified volumes.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|3600|60|master|monitor.healthcheck|

### Name: disk_scrub
#### Description

For each available vdisk it will perform a scrub on it if the stored size is three times bigger than the vdisk size.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|storagedriver|monitor.maintenance|

### Name: disk_scrub_schedule
#### Description

Scheduler that runs on master that executes the disk_scrub script to scrub disk with more storage than their specified size.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|0 22 * * *|60|master|monitor.maintenance|

### Name: disks_destroyer
#### Description

Permanently delete disks with status 'TOBEDESTROYED' by putting them in ascending order and deleting upto 100 GB at a time

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|250|master|cloudbroker|

### Name: fix_rebooted_nodes
#### Description

This script ensures all vms and router oses reboot after a node reboot.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|cpunode|monitor.maintenance|

### Name: ipmi_configure
#### Description

This script will configure the network configuration of the IPMI
Incase of failure on a gooxi we return False instead of an exception

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A||monitor.maintenance|

### Name: kill_orphan
#### Description

Delete orphan vm and return diskinfo

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A||monitor.maintenance|

### Name: logs_truncate
#### Description

Find all logs known logs files and executes logs truncate

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A||monitor.maintenance|

### Name: move_all_vms
#### Description

This script will move all vm's around.
#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|master|maintenance|

### Name: node_maintenance
#### Description

This script is executed by the uptime monitor to investigate a node and take the right action to heal it

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|controllernode|monitor.maintenance|

### Name: openvswitch_cleanup
#### Description

Cleans bridge interfaces that are in error state

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|0 0 * * *|60|cpunode|monitor.maintenance|

### Name: ovs_cgroup
#### Description

This script creates an ovs cgroup and assig ovs related processes to it

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|0 * * * *|60|cpunode, storagedriver|monitor.maintenance|

### Name: rabbitmq_fix_node
#### Description

Check the status of rabbitmq

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|180|storagedriver|monitor.maintenance|

### Name: rabbitmq_status
#### Description

Check the status of rabbitmq

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|180|storagedriver|monitor.maintenance|

### Name: set_backend_maintenance_config_cleanup_deleted
#### Description

This script will set the correct auto_cleanup_deleted_namespaces settings for all the backends in the environment
It considers backends without "cache" in the name to be normal backends.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A||upgrade|

### Name: set_cachebackend_maintenance_config
#### Description

This script will set the correct settings for all the cachebackends in the environment
It considers backends with "cachebackend" in the name to be a cachebackend.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A||upgrade|

### Name: sshkey_check
#### Description

This script checks if all the nodes have the sshkey from the other nodes authorized.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|60|N/A|cpunode, storagenode, storagedriver, controllernode|monitor.maintenance|

### Name: stop_start_windows_vms
#### Description

This script will stop and start all the windows VM's.
#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|master|maintenance|

### Name: toggleswitchports
#### Description

Toggle storage ports on the switch

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|180|controllernode|monitor.maintenance|

### Name: transition_check
#### Description

Recover objects stuck in transition states

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|master|monitor|

### Name: vfw_orphan
#### Description

Checks virtual firewall models and delete them if their respective Cloud Spaces are deleted

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|3600|180|master|monitor.sealfhealing|

### Name: vm_cpu_fair_use_policy
#### Description

Checks cpu time and quratines machine according to fair use policy .

If average per 5 min is higher than threshold a warning is sent via email.

if over use presists for longer than warntime  the machine is quarantined to a limit,
this is done for a quarantine time and then unquarantined .

if quarantined again after unquarantine quarantine time doubles for each time.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|cpunode|monitor.maintenance|

### Name: vm_orphan
#### Description

Checks if libvirt still has VMs that are not known by the system. These VMs are called orphan VMs. Takes into account VMs that have been moved to other CPU nodes.
If orphan disks exist, WARNING is shown in the "Orphanage" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|3600|60|cpunode|monitor.sealfhealing|

### Name: volumedriver_update
#### Description

Update disks edge ip and port in case its storagedriver is changed.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|3480|storagedriver|monitor|

### Name: volumedriver_update_schedule
#### Description

Scheduler that runs on master that executes the volumedriver_update script to update disks edge ip and port in case its storagedriver is changed.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|3600|3540|master|monitor.maintenance|