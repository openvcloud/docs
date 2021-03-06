## End User Authorization Model

In order for a user to have access to the **End User Portal** group membership to the system group **user** is required. For more details about group membership, see the **Groups** page in the **Cloud Broker Portal** and the [Groups Documentation](../../CloudBrokerPortal/Groups/Groups.md).

Once access to the **End User Portal** actual privileges are determined by the rights (read, write, admin) granted to the user, this is done at the level of [Accounts](#account), [Cloud Spaces](#cloud-space), and [Virtual Machines](#virtual-machine).


### How ACL works

Account, Cloud Space and Virtual Machines have a list of access control also known as ACL.
An entry in a ACL is called an ACE (access control entry).
An ACE has a property called explicit.

When we add an ACE to an object let's say for example ADMIN on machine we mark this ACE as explicit, however inside the API we create inexplicit (explicit = false) ACE rules for it's parent objects being account and cloudspace which READ access. This is so that the person who got access on the machine can see which cloudspace/account it belongs to.

An inexplicit R right is NOT able to list ALL objects under need this object, an explicit R right can see all objects under need.

<a id="account"></a>
### Account

#### Read (R):

- account.get() (viewing the account settings)
- account.list() (listing only the accounts the user has access to)
- account.getCreditBalance() (in earlier versions)
- account.getCreditHistory() (in earlier versions)

\+ ALL **Read** actions of **Cloud Space** and **Virtual Machine**

#### Write (RCX):

- ALL **Read** actions of **Account**
- account.update() (changing account settings)
- cloudspace.create()
- machine.createTemplate()

\+ ALL **Read/Write** actions of **Cloud Space** and **Virtual Machine**

#### Admin (ARCXDU):

- ALL **Read/Write** actions of **Account**
- account.addUser()
- account.deleteUser()
- account.update()

\+ ALL **Admin/Write/Read** actions on **Cloud Space** and **Virtual Machine**


<a id="cloud-space"></a>
### Cloud Space

#### Read (R):

- cloudspace.get() (viewing the cloud space settings)
- cloudspace.list() (only the cloud spaces the user has access to)
- machine.list()
- portforwarding.list() (for cloudspace)

\+ ALL **Read** actions of **Virtual Machine**

#### Write (RCX):

- ALL **Read** actions of **Cloud Space**
- cloudspace.deploy()
- cloudspace.getDefenseShield()
- machine.create()
- machine.importToNewMachine()
- portforwarding.create()
- portforwarding.delete()
- portforwarding.update() (Change/delete port forwards for all virtual machines in this cloud space)
- machine.clone()
- machine.delete()
- machine.addUser()
- machine.deleteUser()
- machine.updateUser()

\+ ALL **Read/Write** actions of **Virtual Machine**

#### Admin (ARCXDU):

- ALL **Read/Write** actions of **Cloud Space**
- cloudspace.addUser()
- cloudspace.updateUser()
- cloudspace.deleteUser()
- cloudspace.delete()
- cloudspace.update()

\+ ALL **Admin/Write/Read** actions of **Virtual Machine**


<a id="virtual-machine"></a>
### Virtual Machine

#### Read (R):

- machine.get()
- machine.listSnapshots()
- machine.getConsoleUrl()
- machine.getHistory()
- machine.listExports()
- machine.list() (only for virtual machines user has access to)
- portforwarding.list() (for machine)

#### Write (RCX):

- ALL Read actions of Virtual Machine
- machine.addDisk()
- machine.backup()
- machine.snapshot()
- machine.rollbackSnapshot()
- machine.update()
- machine.export()
- machine.list() (only for virtual machines user has access to)
- machine.start()
- machine.stop()
- machine.pause()
- machine.resume()
- machine.reboot()
- machine.delDisk()
- machine.deleteSnapshot()
- portforwarding.add()
- portforwarding.delete()
- portforwarding.update()

#### Admin (ARCXDU):

\+ ALL **Write/Read** actions of **Virtual Machine**
