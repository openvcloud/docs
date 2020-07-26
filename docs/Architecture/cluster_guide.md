# Architecture guide 

This document includes brief introductory information about all the **pods** running in the **Kubernetes** cluster orchestrated by controller nodes ***ctrl-01***, ***ctrl-02*** and ***ctrl-03***. See [connect to environment](../Sysadmin/Connect/connect) for information how to connect to the controllers.

> Use the following configurations for ovc.conf file in case you use ovcli tool. 
>
> [environments]  
> greenitglobe.development.environments.local = http://172.17.1.1  
> greenitglobe.environments.be-g8-3 = be-g8-3.gig.tech  
> greenitglobe.environments.be-loc-dc01-001 = be-loc-dc01-001.gig.tech  

Once you're inside the controller, list the running pods by running the command  

```kubectl get pods ``` 

**Sample output**:

![image-20200721123847093](/opt/code/git.gig.tech/openvcloud/openvcloud/architecture/image-20200721123847093.png)



#### Nodes 

##### agentcontroller-*
This pod is in charge of orchestration of jobs. In case a job is required to run on another node, the agentcontoller takes care of that. It'll delegate the queuing of the task to the services running on the target node. 

##### grafana-*

Takes care of the visualization of the time series data. This is useful for displaying visually appealing graphs depicting user consumption, utilization, or other time-series based data. However it doesn't hold the data, but rather it communicates with Influx db where the data is stored. 

##### influxdb-* 

This is a database instance optimized for time-series data. It holds the data associated with utilization and billing, and serves it to the [grafana](# grafana-56cb6b76b6-mlxwl) instance where this data is visualized.

##### 
##### jsagent-*

This is an agent that's capable of queuing and running [jumpscripts](#Jumpscripts), however this is for jumpscripts that are not node-specific. That means that the jumpscripts executed by this pod are not associated with a particular node, but instead is concerned with general purpose jumpscripts. It's worth noting that jumpscripts that are specific to a node are handled by a dedicated  [jsagent](#Jsagent) instance running on that particular node. 

##### management-*

Useful for the operations team. Handles tasks like setting up new hardware nodes and so on. 

##### mongo-*
This is used to store the metadata of the cloud. All the data that's needed for running VMs, images, users, accounts, etc. are stored here. You can see that there are 3 instances of mongo db but this is for redundancy and fail-proof purposes. It's worth noting that you'll never directly work with these instances. Instead, you'll be working with the [Osis instance](#osis-*) which is a wrapper around mongodb that acts like mongo so you can query it normally, but handles other tasks for redundancy for example.  

##### nginx-*

This is used as a proxy server that is exposed to the users. That said, this instance will take the requests from the user's front end and then pass them to the cloudapi where they get processed. The nginx is responsible for handling https traffic and has the certificates of the domains configured for `ovs` `defensehield` and `console`.

##### osis-*

A wrapper around [mongodb](#mongo-*). It can be queried normally as any other mongodb but it takes care of the 3 mongodb instances where data actually end up being stored. 

##### ovc-versions-*

This is an nginx instance serving the release manifest for openvcloud. This is used to know if there are new releases available and what they contain

##### portal-*

This is the actual backend of the portal that's serves the admin and end-user portal's API. It is built on the jumpscale7 framework, at the time of this writing.

##### pxeboot-*

This pod contains several containers
1. for dhcp of the management network including a tftp boot for pxebooting the nodes
2. a small http server for hosting the install OS image for (re)installing the nodes
2. and nginx server hosting an apt respository containing all the deb packages a g8 needs

##### qa-*

Used by the dev team for quality assurance tests. 

##### redis-*

Handles caching and queuing the jobs. There are also dedicated redis instances on each nodes, similar to the jsagent case, that are used for job queues. 

##### stats-collector-*

Collects statistics about the nodes, such as utilization of resource. Aggregates useful data for billing and other statistical calculations. 

##### uptime-monitor-*

Monitors the uptime of the nodes. 

##### zero-access-*

Handles SSH-ing into the nodes. It'll provide a temporary user that's associated with your account every time you need to SSH into g8 or the actual cloud. 
These ssh session are monitor (replayable) and searchable


#### Misc

##### Jumpscripts

These are python scripts that do specific jobs on a node, such as creating a VM, allocating diskspace, etc.

##### Jsagent

This is an agent that queues the execution of jumpscripts. It receives a request with the name of a particular jumpscript and it'll take care of the rest, then reports back the result of executing that script. 

