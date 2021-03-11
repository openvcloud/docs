## collectors_reality

### Name: machine_monitoring
#### Description

Gathers statistics about all virtual machines, visualized in the Grid Portal.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|N/A|N/A|node|monitoring.machine|

### Name: network_gathering
#### Description

Gathers information about the NICs, visualized in the Grid Portal: Grid Node > NICS > NIC Details page.

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|300|N/A|node|info.gather.nic|

### Name: switch_connections
#### Description

Gathers network connectiosn

#### Options

|Enabled|Period|Timeout|Roles|Category|
|-------|------|-------|-----|--------|
|True|300|60|master|collect.switch|