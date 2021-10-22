In an on-premises solution, the namespace originally referred to the location of your mailbox. In a global organization, a namespace lets a user connect to the mailbox closest to them. The mailbox had a primary location and often a failback location for resiliency. You'll use the same model in on-premises, hybrid, and cloud-based deployments. There are two namespace models you can use to configure client behavior when connecting to mailboxes.

## Bound namespace model

In a bound model, one datacenter contains an active copy of the mailboxes for one Database Availability Group (DAG), and the other datacenter contains the passive copies. Another DAG has active and passive mailboxes in the reverse datacenters. Each datacenter has a namespace to direct traffic to the correct location. Traffic is only routed to the fallback datacenter if the primary datacenter fails.

## Unbound namespace model

In an unbound model, the namespaces are deployed across two datacenters and in this scenario, there is no active and passive instance. The user can connect to either datacenter. A single namespace spans both datacenters. 

The recommended approach is to use the unbounded model, deploying a single Exchange namespace per client protocol for the site resilient datacenter pair.

## Learn more

- [Namespace Planning in Exchange 2016](https://techcommunity.microsoft.com/t5/exchange-team-blog/namespace-planning-in-exchange-2016/ba-p/604072)
- [Exchange Management Shell namespaces](/exchange/client-developer/management/exchange-management-shell-namespaces)
- [Switchovers and failovers](/Exchange/high-availability/manage-ha/switchovers-and-failovers)
