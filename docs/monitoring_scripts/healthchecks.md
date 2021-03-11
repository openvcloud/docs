## healthchecks

### Name: arakoon_collapse-test
#### Description

arakoon collabpse test

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|0 9 * * *|900|storagedriver|monitor.healthcheck|

### Name: arakoon_divergence-scheduler
#### Description

Scheduler that runs on master that executes the check_arakoon_divergence to check for arakoon divergence on the storage cluster.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|0 21 * * 3|N/A|master|monitor.healthcheck|

### Name: arakoon_divergence-test
#### Description

This script will run the arakoon divergence commands on all arakoons.
It checks for arakoon divergence on the whole cluster. Making sure everything is ok.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|||

### Name: check_scrub_failures
#### Description

This script will loop all vdisk and check if there were scrubbing failures lately 
and if the vdisk got scrubbed.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|||

### Name: check_scrub_failures_scheduler
#### Description

Scheduler that runs on master that executes the check_scrub_failures to check scrub failures on the storage cluster.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|0 23 * * *|60|master|monitor.healthcheck|

### Name: connections_tracker
#### Description

Monitors if connections exceeded 80% of allowed connections
Problems are reported in the "Network" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|60|cpunode, storagenode, controllernode|monitor.healthcheck|

### Name: cpu_ctxpy_check
#### Description

Checks the number of CPU context switches per second. If higher than expected an error condition is thrown.

Currently throws:
- WARNING if more than 1M context switches/s
- ERROR if more than 600k context switches/s

Result will be shown in the "System Load" section of the Grid Portal / Status Overview / Node Status page.

TODO : check these values, specifically if amount of cores per CPU is growing

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|node|monitor.healthcheck|

### Name: cpu_mem_core_check
#### Description

Checks average memory and CPU usage/load. If average per hour is higher than expected an error condition is thrown.

For both memory and CPU usage throws WARNING if more than 80% used and throws ERROR if more than 95% used.

Result will be shown in the "System Load" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|node|monitor.healthcheck|

### Name: db_check
#### Description

Checks status of MongoDB database on Master. If not running an error condition is thrown.
Result will be shown in the "Databases" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|600|60|master|monitor.healthcheck|

### Name: deployment_test
#### Description

Tests every predefined period (default 30 minutes) whether test VM exists and if exists it tests write speed. Every 24hrs, test VM is recreated.
Result will be shown in the "Deployment Test" section of the Grid Portal / Status Overview / Node Status page.
Generates warning if write speed is lower than 50 MiB / second.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|cpunode|monitor.healthcheck|

### Name: disk_usage_check
#### Description

Checks status of all physical disks and partitions on all nodes, reporting back the free disk space on mount points.

(except if / of mount point contains .dontreportusage - which is needed as an exception for read and write cache for OVS)

Throws WARNING per mount point if >90% used, throws ERROR per mount point if >95% used.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|60|20|node|monitor.healthcheck|

### Name: eco_check
#### Description

Checks the number of error condidtions filed: if more than 5 are filed per hour will go into warning state,
and into error state if it exceeds 10 per hour

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|20|master|monitor.healthcheck|

### Name: glusterfs_check
#### Description

Checks that glusterfs server is running on the controller node and that each node in the cluster can see the other nodes.
The script also checks for the consumed storage and report based on the state.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|30|controllernode|monitor.healthcheck|

### Name: heartbeat_check
#### Description

checks nodes heartbeats.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|600|60|master|monitor.healthcheck|

### Name: ipmi_check
#### Description

Check if IPNI of all nodes are available

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|600|60|master|monitor.healthcheck|

### Name: ipmi_checks
#### Description

Checks the power redundancy of a node using IPMItool.
Result will be shown in the "Hardware" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|30|cpunode, storagenode|monitor.healthcheck|

### Name: ipmi_checks_controller
#### Description

Checks the power redundancy of a controller node using IPMItool.
Result will be shown in the "Hardware" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|controllernode||

### Name: ipmi_controller_scheduler
#### Description

Runs the ipmi check on the controller nodes.
Since the controllers share the same hardware, if the check succeeds on one node, the failed check won't be reported.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|600|master|monitor.healthcheck|

### Name: iptables_check
#### Description

Chekc that iptables is configured correctly

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|60|controllernode|monitor.healthcheck|

### Name: kube_nodes
#### Description

This script checks kubernetes pods

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|60|master|monitor.healthcheck|

### Name: kube_pods
#### Description

This script checks kubernetes pods

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|60|master|monitor.healthcheck|

### Name: network_check
#### Description

Check that nodes are in the expected networks with correct IPS and mac addresses

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|3600|60|controllernode, cpunode, storagenode|monitor.healthcheck|

### Name: network_load
#### Description

Check the bandwith consumption of the network

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|180|60|storagenode, storagedriver, cpunode|monitor.healthcheck|

### Name: networkbond_check
#### Description

Monitors if a network bond (if there is one) has both (or more) interfaces properly active.
Problems are reported in the "Hardware" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|60|node|monitor.healthcheck|

### Name: networkid_check
#### Description

Checks the status of the available networkids.
Result will be shown in the "Network" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|1800|60|master|monitor.healthcheck|

### Name: networkperformance
#### Description

Tests bandwidth between storage nodes, volume drivers and itself

Generates a warning if bandwidth is below 50% of the maximum speed
Generates an error if bandwidth is below 10% of the maximum speed


#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|60|storagenode, storagedriver, cpunode|monitor.healthcheck|

### Name: networkstability
#### Description

Tests network between cpu and storage nodes
Make sure all types of network can reach eachother
Ping nodes for 10 times
When less then 90% produce a warning
When less then 70% procede an error
When timings are more then 10ms produce a warning
When timings are more then 200ms produce am error
Futhermore it makes sure that all nics in network have same MTU
Otherwise produces an error message

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|300|60|storagenode, storagedriver, cpunode|monitor.healthcheck|

### Name: nodestatus
#### Description

Checks the status of each node.

ERROR state is automatically attributed to a node by OpenvCloud - this is done if a specific action cannot be executed anymore on the Node.

Result will be shown in the "Node Status" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|60|cpunode, storagenode|monitor.healthcheck|

### Name: openfd_check
#### Description

Checks the number of open file descriptors for each process.
Result will be shown in the "System Load" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|60|30|node|monitor.healthcheck|

### Name: ovs_healthcheck_executor
#### Description

Calls the standard Open vStorage health checks, see: https://github.com/openvstorage/openvstorage-health-check
Result will be shown in the "OpenvStorage" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|590|node||

### Name: ovs_healthcheck_intermediate
#### Description

Calls the standard Open vStorage health checks, see: https://github.com/openvstorage/openvstorage-health-check
Result will be shown in the "OpenvStorage" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|600|590|storagedriver|monitor.healthcheck|

### Name: ovs_healthcheck_intermediate_controller
#### Description

Calls the standard Open vStorage health checks, see: https://github.com/openvstorage/openvstorage-health-check
Result will be shown in the "OpenvStorage" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|600|590|master|monitor.healthcheck|

### Name: ovs_healthcheck_long
#### Description

Calls the standard Open vStorage health checks, see: https://github.com/openvstorage/openvstorage-health-check
Result will be shown in the "OpenvStorage" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|590|storagedriver|monitor.healthcheck|

### Name: ovs_healthcheck_long_controller
#### Description

Calls the standard Open vStorage health checks, see: https://github.com/openvstorage/openvstorage-health-check
Result will be shown in the "OpenvStorage" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|590|master|monitor.healthcheck|

### Name: ovs_healthcheck_short
#### Description

Calls the standard Open vStorage health checks, see: https://github.com/openvstorage/openvstorage-health-check
Result will be shown in the "OpenvStorage" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|180|120|storagedriver|monitor.healthcheck|

### Name: ovspackages
#### Description

Get OVS packages.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|storagedriver||

### Name: public_access_check
#### Description

Checks the access to the public network from the controller by tcp connection to google.com

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|60|controllernode|monitor.healthcheck|

### Name: publicipswatcher
#### Description

Checks the status of the available public IPs.
Result will be shown in the "Network" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|1800|60|master|monitor.healthcheck|

### Name: qemulogs_check
#### Description

Inspects the qemu log files of running VMs and reports if there was any errors.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|300|60|cpunode|monitor.healthcheck|

### Name: rabbitmq_partition_check
#### Description

Check if there are partition issues in RabbitMQ. If issues were found it will restart RabbitMQ. 

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|900|180|storagedriver|monitor.healthcheck|

### Name: raid_check
#### Description

Checks whether all configured RAID devices are still healthy.
Result will be shown in the "Hardware" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|60|node|monitor.healthcheck|

### Name: redis_usage_check
#### Description

Checks Redis server status.
Result will be shown in the "Redis" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|600|60|node|monitor.healthcheck|

### Name: routeros_check
#### Description

Checks the status of RouterOS.
Result will be shown in the "Network" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|cpunode|monitor|

### Name: routeros_check_schedule
#### Description

Scheduler that runs on master to check for dead RouterOS devices.


#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|master|monitor.healthcheck|

### Name: services_check
#### Description

Check that all openvcloud/openvstorage services are up and running on the nodes.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|120|controllernode, cpunode, storagenode|monitor.healthcheck|

### Name: storage_check
#### Description

Checks the utilized capacity on the OVS backends and the objectspaces. 
Reports warning if any OSD or backend exceeds 80%  
Reports error if any OSD or backend exceeds 90%

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|600|60|master|monitor.healthcheck|

### Name: swap_used_check
#### Description

Checks the amount of swap used by the system, and throws an error if higher than expected.

Currently throws:
- WARNING if more than 10 GB
- ERROR if more than 14 GB

Result will be shown in the "System Load" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|node|monitor.healthcheck|

### Name: teleport-check
#### Description

Checks that teleport is running and with the correct config.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|30|controllernode|monitor.healthcheck|

### Name: temp_check
#### Description

Checks the CPU + disk temperature of the system.
Result will be shown in the "Temperature" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|60|node|monitor.healthcheck|

### Name: threads_check
#### Description

Checks the number of threads, and throw an error if higher than expected.

Currently throws
- WARNING if more than 18K threads
- ERROR if more than 20K threads

Result will be shown in the "System Load" section of the Grid Portal / Status Overview / Node Status page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|node|monitor.healthcheck|

### Name: uptime_daemon
#### Description

This script checks the uptime daemon

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|60|cpunode, storagenode|monitor.healthcheck|

### Name: vdisk_checker
#### Description

check 'destroyqueuetimestamp' of disks in 'TOBEDESTROYED' status and create an error if it is there for more than 7days and warning if it is there for more than 2days

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|master|monitor.healthcheck|

### Name: vgw_check
#### Description

Checks the status of our virtual gateways on the node.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|cpunode|monitor.healthcheck|

### Name: vm_disk_check
#### Description

Checks the disks of the virtual machines.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A||monitor.vms|

### Name: vm_disk_ratio
#### Description

Check if number of disks exceeded 6 times machines

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|storagedriver|monitor|

### Name: vm_disk_ratio_schedule
#### Description

Scheduler that runs on master to check for disks/vms ratio
Generates warning if number of disks reached 6 times or more than number of machines.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|30 * * * *|60|master|monitor.healthcheck|

### Name: vm_network_load
#### Description

Check the bandwith consumption of the network utilized by the virtual machine
> 8k packets WARNING
> 10k packets  ERROR

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|180|60|cpunode|monitor.healthcheck|

### Name: vm_ping
#### Description

Checks whether virtual machine is pingable.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|fw|monitor.vms|

### Name: vms_check
#### Description

Check status of virtual machine.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|60|master|monitor.vms|

### Name: volumedriver_check
#### Description

healthcheck that monitors rouge volumedriver  by checking its threads count and memory consumptio

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|300|250|storagedriver|monitor.healthcheck|

### Name: workerstatus_check
#### Description

Monitors the workers, checking if they report back on regular basis report to their agent for new tasks.

Throws ERROR if WORKERS waits longer than expected:
For Default queue > 2 mins
For IO queue > 2 hours
For Hypervisor queue > 10 mins
For Process queue > 1 min

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|600|60|node|monitor.healthcheck|