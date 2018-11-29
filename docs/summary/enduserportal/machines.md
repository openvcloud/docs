# Machines

The **Machines** page is where you create and manage virtual machines.

In order to be able to create a machine, you need to have access to a virtual datacenter.

Within the **End User Portal** you can discover to which virtual datacenters you have access by clicking the second link in the top menu bar.

In the below screenshot for example you can see that the logged in user has access to several datacenters, of which two of them created in the 'Account of Yves':

![](../../.gitbook/assets/virtualdatacenters.png)

In order to have access to other virtual datacenters, or in order to create a new virtual datacenter, you will need to contact a user with administration rights to a cloud account.

Once you have selected a virtual datacenter, you can navigate to the **Machines** page for that virtual datacenter, by clicking the Machines icon or clicking Machines in the right navigation menu:

![](../../.gitbook/assets/virtualdatacenter.png)

In the below screenshot you see that no virtual machines have been created yet in the **demo-vdc** virtual datacenter:

![](../../.gitbook/assets/machines%20%281%29.png)

## Create a new Machine

Clicking **Create Machine** allows you to add a virtual machine to the virtual datacenter.

Give your machine a name:

![](../../.gitbook/assets/machinename.png)

Select an o/s image:

![](../../.gitbook/assets/machineimage.png)

Choose one of the predefined machines packages:

![](../../.gitbook/assets/machinepackage.png)

And finally select the size of the boot drive:

![](../../.gitbook/assets/machinedisksize%20%281%29.png)

As a result you will see this:

![](../../.gitbook/assets/machinecreated.png)

## Actions

The above screenshot shows the **Actions** tab of you newly created machine.

Here you can:

* **Pause**
* **Stop** and **Start**
* **Reboot**
* **Reset**
* **Take Snapshot**
* **Destroy**

## Console

From the **Console** tab you can login to your virtual machine:

![](../../.gitbook/assets/console.png)

You will want to use the very handy paste buttons for the username and initial password.

## Disks

On the **Disks** tab you get add extra data storage to your virtual machine via the **Create disks** subtab:

![](../../.gitbook/assets/createdisks.png)

Below the result after having added two 50 GB disks:

![](../../.gitbook/assets/disks.png)

## Snapshots

Creating snapshots is easy, simply click **Take Snapshot** on the **Snapshots** tab.

Below a screenshot after having created two snapshots:

![](../../.gitbook/assets/snapshots%20%281%29.png)

You can roll back to any of your snapshots or delete a snapshot by clicking one of the actions next to your snapshots.

## Change Log

An history of the changes to your virtual machine is shown on the **Change Log** tab:

![](../../.gitbook/assets/changelog%20%281%29.png)

## Sharing

In the **Sharing** tab you can manage who has access to your virtual machine:

![](../../.gitbook/assets/sharing.png)

A user can either have Read, Read/Write or Admin privileges.

## Port Forwards

On the **Port Forwards** tab all the Port Forwards for your virtual machine are listed:

![](../../.gitbook/assets/portforwards.png)

Adding a port forwarding is simple, just click **Add** and specify the source and destination ports:

![](../../.gitbook/assets/portforward.png)

