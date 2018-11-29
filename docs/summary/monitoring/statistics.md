# Gathering of Statistics

On all physical nodes statistics are gathered and aggregated through Redis.

On the controller of the environment the aggregated data is saved in InfluxDB, from where the statistics can be visualized in the OpenvCloud Operator Portal.

Also check the **JumpScript** page in the **Grid Portal** where you can filter on **monitoring.processes** to see a list of the JumpScripts actually available on your environment:

![](../../.gitbook/assets/jumpscripts%20%282%29.png)

## Script that run on both the CPU nodes and the storage nodes

* **cpu\_physical\_stats.py** gathers CPU statistics \(CPU time, CPU percent, number of threads, number of context switches, number of interrupts\) from physical machines and saves them to Redis
* **disk\_physical\_stats.py** gathers statistics about the physical disks
* **memory\_physical\_stats.py** gathers statistics about the memory of the physical machines
* **network\_physical\_stats.py** gathers following network statistics from the physical machines:
  * network.throughput.outgoing
  * network.throughput.incoming
  * network.packets.tx
  * network.packets.rx
* **temp\_stats.py** checks the \(CPU/disk\) temperature of the system

## Scripts that run only on the CPU nodes

* **cpu\_virtual\_stats.py** gathers statistics about CPU utilization on the virtual machines
* **disk\_virtual\_stats.py** gathers statistics \(iops.read, iops.write, throughput.read, throughput.write\) about virtual disks
* **network\_virtual\_stats.py** gathers following network statistics from the virtual machines:
  * network.throughput.outgoing
  * network.throughput.incoming
  * network.packets.tx
  * network.packets.rx

## Scripts that run only on the storage nodes

* **ovs\_asd.py**
* **ovs\_backend.py** gathers statistics about the Open vStorage backends
* **ovs\_disk\_safety.py** gathers statistics about disk safety and sends this disk safety statistics for each vpool and the amount of namespaces with the lowest disk safety to the database
* **ovs\_proxyperf.py** gathers statistics about Open vStorage proxy performance
* **ovs\_vdisks.py** gathers statistics about the vDisks
* **ovs\_vpool.py** gathers statistics about the vPools

## Other scripts

Next to the above scripts, also following scripts exist:

* **machine\_monitoring.py** gathers statistics about all virtual machines, visualized in the Grid Portal.
* **network\_gathering.py** gathers information about the NICs, visualized in the Grid Portal: Grid Node &gt; NICS &gt; NIC Details page.

Also see the health check scripts, discussed in the [System Health](health.md) section.

