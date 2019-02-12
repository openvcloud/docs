# Virtual Machine Stats
* EndPoint GET `/restmachine/cloudapi/machines/stats`
* request example `/restmachine/cloudapi/machines/stats?include=vdisk-iops&include=vm-iops&include=vdisk-bandwidth&include=cpu&machineId=12&from=epoch&till=epoch`

### This end point retrun machine stats based on the timeframe (from, till) epoch and the include parameters
## params
  * include:
    response will contains the following in it's body only if specified in the include=<parameter> in the request params
    * vdisk-iops: disk iops for each disk in the machine 
    * vdisk-latency: disk latency for disk in machine disks in `MS` 
    * vm-iops: sum(vdisk-iops)
    * vdisk-bandswidh: disk bandwidth for each disk in the machine `KB/S` 
    * vdisk-capacity: disk capacity (including snapshots) in `GB`
    * vm-capaciry: sum(disk capacity or disk in vm disks including snapshots) in `GB`
    * cpu: cpu percentage in use
    * memory: allocated memory in `MB`
    * network: network bandwidth for `IN` and `OUT` for port(interface) of the vm `KB/s`
  * machineid: id of the machine we want to get its stats
  * from: start time to start getting stats starting from this time
  * till: end time to get stats to it 

## response body
```
{
    "time": [epoch1, epoch2, epoch3]
    "series": {
        "vdisk-iops": {
            "vdisk1-id": [25,40,55],
            "vdisk2-id": [45,25,20],
            "vdisk3-id": [40,25,20],
        },
        "vdisk-latency": {
            "vdisk1-id": [25,40,55],
            "vdisk2-id": [45,25,20],
            "vdisk3-id": [40,25,20],
        },
        "vm-iops": [110, 90, 95],
        "vdisk-bandwidth":{
            "vdisk1-id": [25,25,50],
            "vdisk2-id": [100,100,100],
            "vdisk3-id": [50,50,50],
        },
        "vidisk-capacity": {
            "vdisk1-id": [25,25,50],
            "vdisk2-id": [100,100,100],
            "vdisk3-id": [50,50,50],
        },
        "vm-capacity":  [175, 175, 200],
        "cpu": [28,32,43],
        "memory": [1024, 2048, 4096],
        "network": {
            "port1": {
                "in": [3223, 3243, 4334],
                "out": [3223, 3243, 4334]
            },
            "port2": {
                "in": [3223, 3243, 4334],
                "out": [3223, 3243, 4334]
            },
        }
    }
}

```
# cloudspace stats
* EndPoint GET `/restmachine/cloudapi/cloudspaces/stats`
* request example `/restmachine/cloudapi/cloudspaces/stats?include=vdisk-iops&include=vdisk-bandwidth&include=cpu&cloudspaceId=12&from=epoch&till=epoch` 

### This end point retrun cloudspace stats based on the timeframe (from, till) epoch and the include parameters
## params
  * include:
    response will contains the following in it's body only if specified in the include=<parameter> in the request params
    * vdisk-iops: sum(disk iops for each disk in the cloudspace machines disks)
    * vdisk-bandswidh: sum(disk bandwidth for each disk in the cloudspace machines) `MB/S`
    * vdisk-latency: avg(disk latency for disk in cloudspace machines disks) in `MS` 
    * capacity: sum(all disk capacity in cloudspce including snapshots) in `TB`
    * cpu: avg(cpu percentage in use) 
    * memory: allocated memory in `MB`
    * network: network bandwidth for `IN` and `OUT` for port(interface) of the vm `KB/s`
      * usage for vms in and out for all vms in cloudspace in `MB`
      * usage for in and out for vgw and routeros for this cloudspace in `MB`
  * cloudspaceId: id of the cloudspace we want to get its stats
  * from: start time to start getting stats starting from this time
  * till: end time to get stats to it 

## response body
```
{
    "time": [epoch1, epoch2, epoch3]
    "series": {
        "vdisk-iops": [25,40,55],
        "vdisk-latency": [25,40,55],
        "vdisk-bandwidth": [39, 30, 89],
        "cpu": {
            "allocated": [28,32,43],
            "inuse": [20, 15, 30]
        },
        "memory": [1024, 2048, 4096],
        "network": {
            "vms": {
                "in": [3223, 3243, 4334],
                "out": [3223, 3243, 4334]
            },
            "gateways": {
                "in": [3223, 3243, 4334],
                "out": [3223, 3243, 4334]
            },
        }
    }
}
```
# Account stats
* EndPoint GET `/restmachine/cloudapi/accounts/stats`
* request example `/restmachine/cloudapi/accounts/stats?include=storage-capacity&include=cpu&accountId=12&from=epoch&till=epoch` 

### This end point retrun account stats based on the timeframe (from, till) epoch and the include parameters
## params
  * include:
    response will contains the following in it's body only if specified in the include=<parameter> in the request params
    * capacity: sum(all disk capaciry in all cloudspce of the specified account including snapshots) in `TB`
    * vdisk-iops: sum(disk iops for each disk in all cloudspace of the specified accounts)
    * vdisk-latency: avg(disk latency for disk in all cloudspaces of the account disks) in `MS`
    * vdisk-bandswidh: sum(disk bandwidth for each disk in all cloudspace of the account) `MB/S`
    * cpu: avg(cpu percentage in use) 
    * memory: allocated memory in `GB`
    * network: network bandwidth for `IN` and `OUT` all cloudspaces in this account `MB/s`
  * cloudspaceId: id of the cloudspace we want to get its stats
  * from: start time to start getting stats starting from this time
  * till: end time to get stats to it 

## response body
```
{
    "time": [epoch1, epoch2, epoch3]
    "series": {
        "vdisk-iops": [25,40,55],
        "vdisk-latency": [25,40,55],
        "vdisk-bandwidth": [25,40,55],
        "cpu": {
            "allocated": [28,32,43],
            "inuse": [20, 15, 30]
        },
        "memory": [1024, 2048, 4096],
        "network": {
            "in": [3223, 3243, 4334],
            "out": [3223, 3243, 4334]
        }
    }
}
