# External Networks

The **External Networks** page lists all connected external networks:

![](../../.gitbook/assets/externalnetworks%20%281%29.png)

Clicking **+ Add External Network** allows you to add an external network:

![](../../.gitbook/assets/addexternalnetwork.png)

In the above example 50 \(192.168.1.100 -&gt; 192.168.1.150\) of the 256 IP addresses on the external network 192.168.1.0/24 are attached to the location be-g8-4.

Not shown in the screenshot, is the **Account ID** allowing you to make an external network available to only one specific account.

The API that exposes this functionality is part of the **CloudBroker Actors**, available through the **API** page of the **System Portal**, under **cloudbroker\_\_iaas**:

![](../../.gitbook/assets/cloudbroker__iaas.png)

There you will find the **/cloudbroker/iaas/addExternalNetwork** API:

![](../../.gitbook/assets/addexternalnetwork-api%20%281%29.png)

From the **External Network Details** page you can click through to the **External Network Details** page for any of the listed external networks:

![](../../.gitbook/assets/externalnetworkdetails.png)

Under the section **Free IPs** all free IP addresses are listed:

![](../../.gitbook/assets/freeips%20%281%29.png)

Next all **cloud spaces** are listed that use one of the external network IP addresses:

![](../../.gitbook/assets/cloudspaces%20%281%29.png)

Also all **virtual machines** are listed that have been connected directly to one of the external network IP address.

