# OpenvCloud Cluster Setup

Setting up an OpenvCloud cluster is done in following steps:
- [Meet the prerequisites](#prerequisites)
- [Create the configuration file](#create-config)
- [Validate the configuration file](#validate-config)
- [Configure the switches](#configure-switches)
- [Install operation system on the controller nodes](#controller-os)
- [Setup the Kubernetes cluster and deploy the OpenvCloud system containers](#kubernetes-cluster)
- [Access the management container](#management-container)
- [Install the operating systems on the nodes](#os-nodes)
- [Setup the storage nodes](#storage-nodes)
- [Install JumpScale services on nodes](#jumpscale-nodes)
- [Deploy virtual machine images](#deploy-images)


<a id="prerequisites"></a>
## Meet the prerequisites

- Currently supported G8 size:
  - 3 dedicated controller nodes
  - 10 dedicated CPU nodes
  - 4 dedicated storage nodes
- SSH access credentials for all nodes
- Swap needs to be off on each node
- Each node needs to be able to access each other node in the cluster
- Certificates for SSL verification have to be included in YAML config in `certificates` section. Each certificate object should include fields `key` and `crt` containing a private key and a certificate correspondingly. The certificates for different cases should be referenced by name in `ssl` section
- `jsonschema` python library


<a id="create-config"></a>
## Create the configuration file

Installing an OpenvCloud cluster is done based on a single `system-config.yaml` configuration file.

This configuration files describes:
- Switch configuration
- Operating system installations
- Kubernetes cluster running on the controllers, which hosts the OpenvCloud master and and all other controller components
- CPU and storage nodes installation
- ...

The `system-config.yaml` file needs to be stored and maintained in the root of a Git repository on `https://docs.greenitglobe.com`; for each G8 installation there is distinct Git repository on https://docs.greenitglobe.com

The following rules apply:
- The name of the repository should be formatted `env_<<descriptive environment specification>>`, e.g. `env_be-g8-4`
- The repository needs to be put in an organization that represents the partner or customer, e.g. `gigtech` organization for G8s owned by GIG itself, or `digitalenergy` for our Russian partner

Some examples of repositories:
  - https://docs.greenitglobe.com/gigtech/env_be-g8-4
  - https://docs.greenitglobe.com/gigtech/env_se-sto-en01-001
  - https://docs.greenitglobe.com/digitalenergy/env_mr4

An example of a `system-config.yaml` can be found [here](system-config.yaml).

> **Important** A common technique to create a `system-config.yaml` is to make a copy from another environment and start editing. Please make sure to alter the `ssh.private-key` setting, and not just leave the copy from the other environment.


<a id="validate-config"></a>
## Validate the configuration file

Having valid configuration is of course very important. Validating is done with the OpenvCloud environment manager, a.k.a. **Meneja** (Swahili for 'manager'), available on https://meneja.gig.tech.

In [Meneja](https://meneja.gig.tech) you can select the environment you are setting up and click the **Validate configuration** button. When your configuration is valid you'll see the following text appear next to the button: **"The configuration is valid!"***


<a id="controller-os"></a>
## Install the operation system on the controller nodes

On [Meneja](https://meneja.gig.tech) a USB stick can be downloaded that already has the custom configuration for a specific environment. As shown on the screenshot below, there is a link called "Download usb installer image" which results in a bootable ISO file, which can be used to boot from (via the IPMI or via burning it onto a USB stick):

![meneja](images/meneja.png)

After booting up the controller node with the boot image, the user gets a screen with the following options:

![meneja boot menu](images/controller_usb_install.png)

The rest is extremely simple. Just select the right option depending on the controller node that needs to be installed and the rest is completely automatic.

Once you see the following screen, the installation of the controller node has finished. Just unplug the installer image and reboot the machine.

![boot menu](images/controller_usb_install_2.png)

Repeat this procedure for all three controllers.

<a id="configure-switches"></a>
## Configure the switches
configuration of switch should be done like following in system-config.yaml and it will be configured automatically during installaion
Note: uplinks will be configured on Cisco or Mellanox based on the production is true or false in the config
```
network:
  backplane:
    network: 10.107.1.0/24
  # cisco config start 
  cisco: 
  # configure-uplinks explains if we should configure uplinks on this switch or not
  - configure-uplinks: true
    hostname: be-g8-3
    name: 50 port switch
    password: cisco
    # define which ports connected to which device
    ports:
      # total number of ports in the switch
      count: 50
      # ports that are connected to the 3 controllers
      controllers:
        # ports that use it though ipmi to reboot, start and ...etc the nodes
        ipmi: 46-48
        # ports that hold internal traffic through management interfaces
        management: 35,37,13
      # ports that are connected to cpunodes
      cpunodes:
        ipmi: 2-5,26-29
        management: 7-10,31-34
      mellanox: 38,14
      # ports that are connected to storage nodes
      stornodes:
        ipmi: 40,20,19,41
        management: 16-18,39
    # provider-port is the port that connects the switch to the internet
    provider-port: 50
    # switch serial number
    serial_number: DNI202500MU
    # switch-ip defines which ip we should configure the switch with inside the network
    switch-ip:
      address: 10.107.2.201
      netmask: 255.255.255.0
    # trunk-port defines trunk connections to the controllers and other switches
    trunk-ports:
      controllers: 11,12,45
      mellanox: 48,49
    username: cisco
  gateway-management:
    network: 10.199.0.0/22
    vlan: 2314
  ipmi:
    network: 10.107.4.0/24
    vlan: 2311
  management:
    gateway: 10.107.2.254
    network: 10.107.2.0/24
    vlan: 2311
  # mellanox config
  mellanox:
  # ports that connects cpu and storage node
  - nodes:
    - ports: 1-4,7-10
      split: false
    - count: 4
      enable: 3-4
      ports: '5'
      split: true
    # the count config here explains the number of ports to split each to port
    - count: 4
      # which ports are enabled after split
      enable: 1-2
      # which ports are we applying this config to
      ports: '6'
      split: true
  - ports:
      # total number of ports in the switch
      count: 12
  # mlag ip of this switch
    mlag-ip: 122.21.21.13
    name: mellanox-1
    password: admin
  # provider config will be used if configure-uplinks on this switch is set
    provider:
      mlag-channel: 17
      port: 46
      vlan: 2300
  # connection between this switch and other switches
    sw-uplinks:
      cisco-mlx: 11
      mlx-mlx: 12
    switch-ip:
      address: 10.107.2.202
      netmask: 255.255.255.0
    username: admin
  # the second mellanox switch
  - nodes:
    - ports: 1-4,7-10
      split: false
    - count: 4
      enable: 3-4
      ports: '5'
      split: true
    - count: 4
      enable: 1-2
      ports: '6'
      split: true
  - ports:
      # total number of ports in the switch
      count: 12
    mlag-ip: 122.21.21.14
    name: mellanox-2
    password: admin
    provider:
      mlag-channel: 17
      port: 48
      vlan: 2300
    sw-uplinks:
      cisco-mlx: 11
      mlx-mlx: 12
    switch-ip:
      address: 10.107.2.203
      netmask: 255.255.255.0
    username: admin
  # public network vlan
  public:
    gateway: 10.101.0.1
    vlan: 101
    # public connection type either VRRP or IBPGP
    connection-type: VRRP
  storage:
    network: 10.107.3.0/24
    vlan: 2315
  vxbackend:
    network: 10.240.0.0/16
    vlan: 2313


```

<a id="Automatic Installaion">
## Automatic Installion
By running the following command you will have your cluster fully installed and deployed
```
bash  /install.sh -s <PASSWORD> [- u <MANIFESTURL> | -v <VERSION>]
password is the password you enterned on meneja to download the image
```
example
```
bash /install.sh -s rooter123 -v 2.4.6
```
<a id="management-container"></a>
## Access the management container

The management container is used to perform various admin operations on the environment. It is based on the management image and has the `kubectl` tool installed that is needed to perform various Kubernetes related operations. The management container also contains the environment system configuration which is necessary to use the `installer` tool inside the pod. The `installer` tool uses the system config by default and it doesn't need to be specified by the user.

For more details about the `ìnstaller` script see [Installer Script Details](Installer-script.md).

Accessing the management container can be done using **0-access**.

From a web browser open the OpenvCloud portal and go to the **0-access** page at `https://{env name}.demo.greenitglobe.com/cbgrid/0-access`.

![0-access](images/0-access.png)

Choose `management` from the list. You will be directed to a page that will allow you to request access to the pod which will redirect you to a page with instructions about how to access the management container and the remaining time for this session.


<a id="os-nodes"></a>
## Installing the operating system on the nodes

You need to be in management container to perform this operation.

To prepare the CPU and storage nodes with the necessary OS, first start a tmux session and then run the following command:

```bash
installer node action --name all install_os
```

If a node fails during the installation, use the following command to install the node again:

```bash
installer node action --name {node name} install_os
```


<a id="storage-nodes"></a>
## Setup the storage nodes

From the management container execute:

```bash
export ENV_NAME="be-g8-3"
# let's generate the config
python3 /opt/code/git.gig.tech/openvcloud/openvcloud_installer/scripts/ovs/ovs_configurator.py

cd /opt/code/github/openvstorage/dev_ops/Ansible/openvstorage/playbooks/
ansible-playbook -i inventories/$ENV_NAME/inventory preInstall.yml
# this last step is not very bullet proof and might need to be repeated
ansible-playbook -i inventories/$ENV_NAME/inventory full_setup.yml
```

<a id="jumpscale-nodes"></a>
## Install JumpScale services on the OpenvCloud cluster nodes

You need to be in management container to perform this operation.

First start a tmux session. The following command will install the JumpScale services on all OpenvCloud cluster nodes (CPU and storage):

```bash
installer node jsaction --name all install
```

If a node fails during the installation, use the following command to install the node again:

```bash
installer node jsaction --name {node name} install
```

For more details about the `ìnstaller` tool see [Installer Script Details](Installer-script.md).

When done, the environment should be ready to use.

<a id="deploy-images"></a>
## Deploy virtual machine images

To add images [see](../CloudBrokerPortal/Images/Images.md)
