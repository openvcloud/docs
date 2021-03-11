## collectors_stats

### Name: cpu_physical_stats
#### Description

Gathers following CPU statistics from physical machines:
- CPU time
- CPU percent
- Number of threads
- Number of context switches
- Number of interrupts

Statistics are writen to Redis.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|60|N/A|node|monitoring.processes|

### Name: disk_physical_stats
#### Description

Gathers following statistics about the physical disks:
- time_read
- time_write
- count_read
- count_write
- kbytes_read
- kbytes_write
- MB_read
- MB_write
- space_free_mb
- space_used_mb
- space_percent

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|60|N/A|node|disk.monitoring|

### Name: memory_physical_stats
#### Description

Gathers statistics about the memory of the physical machines.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|60|N/A||monitoring.processes|

### Name: network_physical_stats
#### Description

Gathers following network statistics from the physical machines:
- network.throughput.outgoing
- network.throughput.incoming
- network.packets.tx
- network.packets.rx

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|60|N/A|node|info.gather.nic|

### Name: objectspaces_stats
#### Description

Gather consumed storage from the objectspaces

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|300|30|master|monitor.healthcheck|

### Name: ovs_asd
#### Description

Gather statistics about Open vStorage ASD.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|60|storagemaster|disk.monitoring|

### Name: ovs_backend
#### Description

Gathers statistics about the Open vStorage backends.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|60|storagemaster|disk.monitoring|

### Name: ovs_disk_safety
#### Description

Gathers statistics about disk safety and sends this disk safety statistics for each vpool and the amount of namespaces with the lowest disk safety to the database.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|60|storagemaster|disk.monitoring|

### Name: ovs_proxyperf
#### Description

Gathers statistics about Open vStorage proxy performance.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|60|30|storagedriver|disk.monitoring|

### Name: ovs_stats_150sec
#### Description

Scheduler that runs on master to collect OpenvStorage stats

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|60|10|master||

### Name: ovs_stats_60sec
#### Description

Scheduler that runs on master to collect OpenvStorage stats

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|60|10|master||

### Name: ovs_vdisks
#### Description

Gathers statistics about the virtual disks.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|60|storagemaster|disk.monitoring|

### Name: ovs_vpool
#### Description

Gathers statistics about the vPools.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|60|storagemaster|disk.monitoring|

### Name: process_physical_stats
#### Description

Gathers following statistics about specific processes:
- VmRSS
- VmSize

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|60|N/A|node|process.monitoring|

### Name: temp_stats
#### Description

Checks the (CPU/disk) temperature of the system.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|60|30|node|monitoring.processes|

### Name: tor_stats
#### Description

Gathers statistics about the switches

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|300|120|master|monitor.healthcheck|

### Name: virtual_stats
#### Description

Gathers virtual statistics (iops.read, iops.write, throughput.read, throughput.write, ...)

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|60|40|cpunode|monitor.healthcheck|