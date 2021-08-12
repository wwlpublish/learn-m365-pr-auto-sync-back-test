Azure includes several features that help ensure that your Azure Virtual Desktop and infrastructure are resilient. Your organization can include these features in the business continuity and disaster recovery (BCDR) strategy for Azure Virtual Desktop.

## Region pairing

*Azure regions* represent a set of datacenters that are deployed within a latency-defined perimeter and connected through a dedicated regional low-latency network.

All Azure regions are paired with a different region. In a region pair, the regions are never updated simultaneously. Instead, they're updated sequentially. This way, updates will affect only one region.

These region pairs are also used for replication. Storage and many platform as a service (PaaS) solutions are replicated and have failover pairs in the paired region. As part of your BCDR planning, it's important to use region pairing to take advantage of the isolation it provides. This reduces the amount of time it takes to recover from a failure and increase your availability.

## Availability sets

An *availability set* in Azure is a logical grouping capability that you can use to help ensure that the VM resources you place within it are isolated from each other when you deploy them within an Azure datacenter. Availability sets are made up of _update domains_ and _fault domains_.

:::image type="content" source="../media/3-availability-sets.png" alt-text="Diagram depicting fault domains and update domains in an availability set." border="true":::

Update domains ensure that when VM hosts in an Azure datacenter require downtime for maintenance, a subset of your session hosts remain running. When a maintenance event occurs, such as applying a performance or a critical security update, Azure sequences the update through update domains.

Fault domains (FDs) represent physical sections of the datacenter and ensure rack diversity of servers in an availability set. FDs align to the physical separation of shared hardware in the datacenter. If the hardware supporting a server rack becomes unavailable, only that rack of servers would be affected by the outage. When you place your VMs in an availability set, they're automatically spread across multiple FDs. If the hardware fails, only some of your VMs will be affected.

You can use availability set as the default resiliency option for the Azure Virtual Desktop host pool if you have domain controllers in an Azure VM.

## Availability zones

*Availability zones* are independent physical datacenter locations within a region that have their own power, cooling, and networking. By taking availability zones into account when you're deploying resources, you can protect workloads from datacenter outages while maintaining a presence in a particular region. Services such as VMs are _zonal services_, and you can deploy them to specific zones within a region. Other services are _zone-redundant services_, which replicate across the availability zones in the specific Azure region. Both types of zones ensure that an Azure region has no single points of failure.

By using availability zones, you can distribute VMs in the host pool across various datacenters. VMs are still inside the same region, have higher resiliency, and have a higher formal 99.99 percent high-availability service-level agreement (SLA).

:::image type="content" source="../media/3-availability-zones.png" alt-text="Diagram depicting three different availability zones." border="true":::

## Azure Site Recovery

Azure Site Recovery manages the orchestration of disaster recovery in Azure by replicating VM workloads between Azure regions. If an issue occurs at the primary site, Azure Site Recovery invokes the failover to the session hosts in the other region. You can use Site Recovery as part of your BCDR strategy for Azure Virtual Desktop.

As part of your BCDR plan, you can also use Site Recovery to replicate domain controllers, session host VMs, and user and app data across regions to the secondary region. You can add pre-scripts and post-scripts to Site Recovery to fail over non-VM resources and replicate Azure Storage resources.

Site Recovery is also designed to replicate VM workloads from a primary site or region to a secondary site. You can use it to migrate VMs from other environments, such as on-premises infrastructure, to Azure.

:::image type="content" source="../media/3-azure-site-recovery.png" alt-text="Diagram depicting Azure Site Recovery across two different regions." border="true":::

### Snapshots and recovery points

Site Recovery has customizable replication policies that you can use to define the retention history of recovery points and the frequency of snapshots. You create a recovery point from a snapshot of a VM's disk. Two types of snapshots are available:

- **Crash-consistent recovery**: Represents the data that's on disk at the time the snapshot is taken. The default for capturing snapshots is every five minutes.
- **App-consistent recovery**: Captures the same data as crash-consistent recovery, and it includes all in-memory data and in-process transactions. Including the in-memory data enables Site Recovery to help restore a VM and any running apps without data loss. The default time for capturing snapshots is every 60 minutes.

## Azure Backup

Azure Backup is a built-in Azure service that provides secure backup for all Azure-managed data assets. It uses zero-infrastructure solutions to enable self-service backups and restores, with at-scale management at a lower and more predictable cost. You can use Azure Backup to maintain copies of stateful data that allow you to retrieve previous data. You can configure Azure Backup for VMs and Azure Files shares that contain your FSLogix profiles or MSIX app attach.

## User data in OneDrive

You can use Microsoft OneDrive to redirect well-known folders (such as Desktop, Documents, Pictures, Screenshots, and Camera Roll), if present. This redirection creates resilience for these special folders.

## Virtual network

As a part of your BCDR strategy for Azure Virtual Desktop, you need to set up a virtual network in your secondary region. You can create a virtual network manually and then set it up with peering with the primary network. You can also use Site Recovery to set up the virtual network in the failover region and preserve your primary network's settings.

>[!Note]
> Virtual networks that are created in different regions can't have overlapping IP address ranges, and IP addresses will change at failover.

## Domain Name System (DNS)

Active Directory authentication must be available in the disaster recovery region, or connectivity to the on-premises domain must be guaranteed. To ensure that VMs locate domain controllers for authentication, the virtual network in disaster recovery should be set up with a custom DNS server that can resolve active directory services.
