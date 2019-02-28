# Kubernetes migration

The update from 2.4.6.x to 2.4.7 will have a different procedure than other updates. This is due to the introduction of a new kubernetes version which will require tearing down and rebuilding the cluster as well as stop using syncthing and host paths as persistent volumes and replacing them with GlusterFs.

Currently the version used for kubernetes is 1.8.5, besides not being up to date the cluster was configured using our own installation script which caused some configuration to not be set up properly. The 1.13.1 installation will be done using kubespray.

## Upgrade path

Since this upgrade will tear down the cluster, the only way to check the update is by following the docker logs of the container `kube-migrator` on the first controller node.

The upgrade will start from the versions page as usual until the message to check the container logs which means that the container is spawned and will start the migration process. Before the docker runs, both the versions and config manifest are dumped under `/var/ovc/manifests`.

The process is as follows:

- The upgrade job will check the version of the cluster if it is `1.8.5` it will dump the files and trigger the container and terminate

- The container will do the following:

  - Install gluster on all threee controller nodes
  - Backup the ovs credentials in `/var/ovc/manifests/ovs-cred.json`
  - Tear down the cluster, by removing all the kubernetes resources from each controller node:
    - Resetting each node and deleting the kubernetes files and binaries
    - Removing the etcd service
    - Removing the kubernetes firewall rules
  - The container will then change the docker config and restart the docker service there on the other controller nodes
  - It will then restart the docker on the first node and then triggering the second container which will continue the          installation
- The second container will do the following:
  - It will migrate the hostpaths to a gluster volume
  - Will start the normal update process but instead of updating the cluster it will install it with kubespray

The cluster should be up after that with all three nodes having gluster service running and with kubernetes version 1.13.1 and with role master. 
