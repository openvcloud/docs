# Installer script manual

The installer script is used to:

* Setup the Kubernetes cluster on the controller nodes and deploy the OpenvCloud system containers on the Kubernetes cluster
* Install JumpScale services on the OpenvCloud cluster nodes
* Execute IPMI and JumpScale commands on the OpenvCloud cluster nodes
* Deploy virtual machine images

The script is used as follows:

```bash
installer --version {installation version} --config {system config file path} <command> <subcommand> [other options]
```

With `--version` you specify the required available release to be installed, e.g. `2.3.0`.

With `--config` you specify the path to the system configuration file, typically `system-config.yaml`. This file contains all the necessary information for a successful installation using the YAML format. For more details see [Configuration File Details](../system-config.md).

The script takes following commands:

* [cluster](installer-script.md#cluster)
* [node](installer-script.md#node)
* [storage](installer-script.md#storage)
* [image](installer-script.md#image)

## cluster <a id="cluster"></a>

The `cluster` command is used to perform actions on the Kubernetes cluster which includes deploying, updating and upgrading the Kubernetes cluster and its workloads.

There are four `cluster` subcommands:

* [cluster deploy](installer-script.md#cluster-deploy)
* [cluster resources](installer-script.md#cluster-resources)
* [cluster updatedomain](installer-script.md#cluster-updatedomain)
* [cluster upgrade](installer-script.md#cluster-upgrade)

### cluster deploy <a id="cluster-deploy"></a>

The command `cluster deploy` will use the **JumpScale Prefab module for Kubernetes** to install the Kubernetes cluster and deploy the OpenvCloud pods.

Following options are available

* `--configure-cluster` specifies to setup the Kubernetes cluster or not
* `--no-configure-cluster` specifies to only OpenvCloud pods

Usage

```bash
    installer --config system-config.yaml cluster deploy
```

### cluster resources <a id="cluster-resources"></a>

The `resources` command is used to handle Kubernetes resource files.

There are four `cluster resources` subcommands:

* [`apply`](installer-script.md#cluster-resources-apply)
* `applyall`     Apply all kubernetes resources
* `write`        Rewrite all templates
* [`writeconfig`](installer-script.md#cluster-resources-writeconfig)

### cluster resources apply <a id="cluster-resources-apply"></a>

Apply a specifified kubernetes resource Following options are available:

* `--path` path to template

### cluster resources writeconfig <a id="cluster-resources-writeconfig"></a>

The command `cluster resources writeconfig` is used to create Kubernetes **ConfigMaps** from the specified configuration file. `configmap` is the specified configuration that can be mounted to the Kubernetes pods when the application needs information from the config file to perform its operations. This is already handled using the above command but this command can be used if it is required to update the ConfigMap with new config data.

Usage is as follows

* Write or update system-config in Kubernetes ConfigMap based on YAML file:

  ```bash
    installer --config system-config.yaml cluster resources writeconfig
  ```

* Rewrite kube resources from template:

  ```bash
    installer --config system-config.yaml cluster resources write
  ```

### cluster updatedomain <a id="cluster-updatedomain"></a>

The command `cluster updatedomain` is used to update the SSL certificates and the domain of the environment. This is done by updating the `environment` and/or `certificates` sections in the passed configuration file. `ssl` section needs to be updated with a new certificate names for the certificate update, the `subdomane` and `basedomain` for the update domain. If adding a new certificate, `certificates` section needs to be updated with a new certificate, referenced from `ssl` section.

### cluster upgrade <a id="cluster-upgrade"></a>

Upgrade cluster, update all nodes and cluster and update kubernetes resources.

## node <a id="node"></a>

The `node` command is used to execute IPMI and JumpScale actions on the CPU and storage nodes in the OpenvCloud cluster.

Subcommands of `node`:

* `action`    Will apply the action on storage and cpu...
* `jsaction`  Will apply the action on all nodes \(cpu,...
* `update`    Update code and restart required services on...

Usage is as follows:

```bash
installer --config system-config.yaml node action --name node_name <action>
```

with `--name` you specify the name of the CPU/storage node, as configured in the configuration file.

Following **IPMI** commands are supported:

* `reboot` reboots the specified node
* `is_up` check whether node is up and running
* `wait_up` waits untill the node is up and running
* `enable_pxe` enables PXE on node
* `disable_pxe` disables PXE on node
* `install_os` installs the operating system on node

Following **JumpScale** commands are supported:

* `install` installs JumpsScale services
* `start` starts JumpScale services
* `stop` stops JumpScale services r
* `restart` restart JumpScale services
* `update` updates JumpScale services

## storage <a id="storage"></a>

Subcommands:

* `applyconfig`  Apply storage config

## image <a id="image"></a>

The `image` command is used to install virtual machine images on the OpenvCloud cluster.

Usage is as follows:

```bash
installer --config system-config.yaml image deploy --name image_name
```

With `--name` you specify the AYS template of the image package to deploy.

