# Monitoring of the physical nodes

This is a new system to detect physical nodes failures and to take the required actions, it consists of two components:
- Uptime Daemon
- Uptime Monitor

## Uptime Daemon

UDP gevent based daemon, running on all **cpu**/**storage** nodes and it has two roles:

- Sends a 16 byte random uuid every second (via the backplane and management interfaces) to the uptime daemons of the other nodes. When it does not receive an echo from a certain node within 5 seconds, it notifies the **Uptime monitor** that this node is not responding.

- echos all the messages coming from the other uptime daemons, to prove that its node is alive.

## Uptime Monitor
UDP gevent based service, running on a kubernetes pod that receives notifications from the uptime daemons when they fail to get an echo form a certain other uptime daemon. When the **Uptime monitor** discovers that more than **50 %** of the uptime daemons report that a certain node is not responding, it starts investigating by running a jumpscript from one of the controller agents.

The jumpscript will try to connect to the node via ssh and if that fails, it will shutdown the node using the IPMI tool then put the node into maintenance.