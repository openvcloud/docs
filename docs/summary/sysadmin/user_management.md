# User Management

As documented in the [section about the Users page](../cloudbrokerportal/users.md) user management is done from the **Users** page wich is both accessible from the **Cloud Broker Portal** and **System Portal**.

A user is minimally member of "user" and/or the "admin" group:

* In order to have access to **End User** portal, you need at least "user" group membership
* Access to all other portals, such as the **Cloud Broker Portal**, requires at at least "admin" group membership

See the [section about Groups](../cloudbrokerportal/groups.md) for more details about the other groups, particullary the "level 1", "level 2" and "level3" groups are important to understand when operating an OpenvCloud environemnt.

See the [section about the End User Portal Authorization Model](../enduserportal/authorizationmodel.md) to learn about the actual \(read, write, admin\) rights that need to be granted to end users at the level of accounts, cloud spaces, and virtual machines.

Managing who has read, write or admin access at the account level can only be done via the **Accounts** page in the **Cloud Broker Portal**, as documented in the [section about Accounts](../cloudbrokerportal/accounts.md).

Managing who has read, write or admin access at the cloud spaces and virtual machines level is done in the **End User Portal**, as documented in the [sections about Cloud Space Settings](../enduserportal/cloudspacesettings.md) and the [section about Machines](../enduserportal/machines.md) respectivelly.

## Quotas

Limiting the maximum available cloud capacity is done at two levels:

* Total capacity available at the level of an account, see the [section about Accounts](../cloudbrokerportal/accounts.md) for more details
* Total capacity availalble at the level of virtual datacenter \(cloud space\), see the [section about Cloud Spaces](../cloudbrokerportal/cloudspaces.md) for more details

Currently you can not limit the maximum available capacity to a virtual machine or user.

## ItsYou.online

For all interactions with an OpenvCloud environment through the Cockpit API, Cockpit Portal, and Cockpit Chatbot authentication and authorization is managed by Itsyou.online.

