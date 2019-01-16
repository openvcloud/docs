# Cloud capacity units

OpenvCloud defines 4 capacity units that are used for billing the end customer:
- CU or compute units
- SU or storage units
- TU or transaction units
- NU or network units

## CU aka compute units
- type: **allocation**
- definition: 1 vm with 4GiB of memory and 2 virtual CPU's. CU's are calculated on per vm, per cloudspace, per account and per g8 towards the upper value of the memory / virtual cpu combination. 

Some examples:
- a vm with **4GiB** of memory and **1** virtual CPU consumes **1CU**
- a vm with **3GiB** of memory and **2** virtual CPU's consumes **1CU**
- a vm with **4GiB** of memory and **2** virtual CPU's consumes **1CU**
- a vm with **5GiB** of memory and **2** virtual CPU's consumes (5/4) **1.25CU**
- a vm with **4GiB** of memory and **3** virtual CPU's consumes (3/2) **1.5CU**
- a cloudspace with 3 vm's that have a combined memory of **15GiB** and **8** virtual CPU's consumes (8/2) **4CU**

## SU aka storage units
- type: **allocation**
- definition: 1TiB of allocated vdisk capacity

E.g. a vm with 1 bootdisk of 12 GiB and 1 datadisk of 512 GiB consumes ((12+512)/1024) **0.52SU**

## TU aka transaction units
- type: **allocation**
- definition: 400 allocated iops

E.g. a vm with 1 bootdisk limited to 2000 iops and 1 datadisk limited to 10000 iops consumes ((2000+12000)/400) **35TU**

## NU aka network units
- type: **consumption**
- definition: 1TiB consumed traffic from & towards the virtual firewall or external ip address on a virtual machine