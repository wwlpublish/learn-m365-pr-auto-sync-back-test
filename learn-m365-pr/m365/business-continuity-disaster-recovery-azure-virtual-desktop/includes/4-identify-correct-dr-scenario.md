Your organization must prepare the correct disaster recovery protection to limit the impact of a datacenter failure or a regional outage. Setting the correct protection strategy depends primarily on different failure scenarios that might affect your Azure Virtual Desktop's functionality.

## Objectives and metrics

The disaster-recovery process requires coordination between each of the procedures undertaken to bring an organization back to full operation. What brings these procedures together collectively is the presence of common, clearly defined service-level objectives. DR services should include the following:

- Recovery Point Objective (RPO) - The minimum allowable amount of data that you must deliver back to clients for the service based around the backed-up assets that are considered to be recovered. Conversely, this amount may be considered the maximum acceptable data loss, expressed as a percentage subtracted from 100.
- Recovery Time Objective (RTO) - The maximum window of time allowable for a restoration process to take place, which may also be considered a measure of how much downtime the organization is willing to afford.
- Retention period - The maximum allowed period of time for a backup set to be retained before it needs to be refreshed and replaced.

RPO and RTO may be perceived as being balanced against one another, so that a customer may decide to allow for longer recovery times to attain higher recovery points. If recovery time is an issue for a customer due to available bandwidth or risk of downtime, that customer may not be able to achieve a high RPO.

The rest of the unit will explore three different failure scenarios and how to prepare BCDR for Azure Virtual Desktop:
 - Scenario 1. Local corruption of data, metadata, or resources
 - Scenario 2. Single datacenter of Availability Zone failure within an Azure region
 - Scenario 3. Azure region outage

## Scenario 1. Local corruption of data, metadata, or resources

Suppose your Azure Virtual Desktop environment is affected by a session host failure or a corruption of the FSLogix profile. In such situations, the most common method of recovery is to restore the profiles from a backup or to rebuild the session host. This unit reviews how each of these methods applies to each Azure Virtual Desktop environment component.

### Azure Virtual Desktop service

The Azure Virtual Desktop service remains fully functional and isn't affected by these failure types. Microsoft is responsible for getting everything back up and running within the provided Service Level Agreement (SLA).

### AD DS and Azure AD DS

Active Directory domain controllers are critical components of Azure Virtual Desktop and must be always accessible. To ensure failure doesn't impact their functionality, make sure that you've created multiple domain controllers. If you have domain controllers in an Azure VM, make sure that you've configured those VMs to be in the same Availability Set. If your domain controllers are running as on-premises computers, you should design the connectivity between your on-premises network and Azure virtual network with redundancy. Use Azure ExpressRoute to manage redundant paths and connections. Back up the Active Directory system state and restore if needed. If you're using Azure AD DS, then Microsoft is responsible for maintaining redundant domain controllers and helping protect them from unplanned failures.

>[!Note]
> To learn more how to protect Azure virtual machines read the following Microsoft Learn module [Protect your virtual machines by using Azure Backup](https://docs.microsoft.com/learn/modules/protect-virtual-machines-with-azure-backup/)

### Host pools

Host pools could become unavailable in the normal course of operation. Host pools deliver Azure Virtual Desktops and apps to users. They're provisioned from the desktop image, so if a failure occurs and a desktop image is available, you can recreate them. You can also use a separate host pool for applications consumed through Azure Virtual Desktop. You should also consider a similar disaster recovery approach for this host pool.

### Virtual Network

Virtual networks are managed services and aren't affected by this type of failure. Azure Virtual Network provides a private IP block where you can deploy all your resources for private connectivity, and you can then secure those resources within a boundary. Therefore, a Virtual Network will never go down or experience an outage in case of a local failure of the resource in a single datacenter.

### FSLogix profiles and MSIX app attach

Depending on your FSLogix storage technology choice, you can configure Azure Backup for Azure Files shares and Azure NetApp Files snapshots. Alternately, you can use the backup service to protect files and folders on server VMs. 

>[!Note]
> To learn more about Azure Backup and how to protect different services running in Azure use the following article [Back up Azure file shares](https://docs.microsoft.com/azure/backup/backup-afs)

### Master images

You might often make changes to desktop images during the normal course of Azure Virtual Desktop environment maintenance. You should maintain backups of master images so you can quickly recover them in the event of any corruption.

## Scenario 2. Single datacenter of Availability Zone failure within an Azure region

An Azure region is a set of datacenters deployed within a latency-defined perimeter and connected through a dedicated regional low-latency network. In case of an outage of a datacenter or zone in an Azure region, your BCDR for Azure Virtual Desktop should include the recommendations listed in the following sections. 

### Azure Virtual Desktop service

The Azure Virtual Desktop service remains fully functional and isn't affected by this kind of failure. Microsoft is responsible for getting everything back up and running within the provided SLA.

### AD DS and Azure AD DS

To avoid a single datacenter failure, deploy at least two domain controllers in an Availability Zone. If you're using Azure AD DS, Microsoft manages the two domain controllers for your tenant in a separate Availability Zone, providing it's supported by the region.

### Host pools

For host pool VM resiliency, you can deploy an Azure Virtual Desktop host pool using Availability Zones for VMs. You can distribute VMs in the host pool across different datacenters that are still inside the same region.

### Virtual network

Virtual networks are a managed service and aren't affected by this failure type. You should ensure that dependable resources are always configured with appropriate network connectivity. For example, using a basic load balancer might be affected by this type of failure since it does not support zone availability.  

### FSLogix profiles and MSIX app attach

Use Azure Files with Premium Zone Redundant Storage to leverage support for Availability Zones. In this scenario, FSLogix profiles and MSIX app attach VHDs remain available if there's a datacenter outage.

### Master images

This kind of failure doesn't affect master images because they become available in another zone.

## Scenario 3. Azure region outage

Failure of complete Azure regions is highly unlike and rare. But you should also be prepared in case such a failure occurs. Consider implementing the following recommendations to implement BCDR for Azure Virtual Desktop.

### Azure Virtual Desktop service

The Azure Virtual Desktop service remains fully functional and isn't affected by this type of failure. Microsoft is responsible for getting everything back up and running within the provided SLA.

### AD DS and Azure AD DS

To prepare for this type of failure, you can expand a managed domain to have more than one replica set per Azure AD tenant. Replica sets can be added to any peered virtual network in any Azure region that supports Azure AD DS.

>[!Note]
> Review the concept and features of Replica sets for Azure Active Directory Domain services on the following link: [Replica sets concepts and features for Azure Active Directory Domain Services](https://docs.microsoft.com/azure/active-directory-domain-services/concepts-replica-sets)

If you use on-premises domain controllers, you'll need to configure connectivity to the virtual network in the new region using either a VPN, ExpressRoute, or a virtual wide area network (Virtual WAN). If you use Azure AD DS, you can create an additional replica set in another region. The virtual network in the additional region that's hosting the new replica set must be able to communicate with the network hosting the primary set of Azure AD DS. We recommend you use peering between virtual networks for intra-site replication between replica sets.

### Host pools

You can deploy an Azure Virtual Desktop host pool in the active-active and active-passive configurations:

- Active-active. With active-active, a single host pool can have VMs from multiple regions. You must combine cloud cache features to actively replicate a user's FSLogix profile across storage in multiple regions. For MSIX app attach use another copy on an additional file share in the other region. VMs in each region should contain the Cloud cache registry to specify the locations. Additionally, you must configure the Group Policies to give precedence to the local storage location. This Azure Virtual Desktop deployment provides the highest efficiency from a user perspective. This is because if there's a failure, users in the remaining region can continue to use the service without having to sign in again. However, this configuration is more costly and more complex to deploy and isn't optimized for performance.

>[!Note]
> Use the following tutorial to configure Cloud Cache to redirect profile containers to multiple providers [Tutorial: Configure Cloud Cache to redirect profile containers or office container to multiple Providers](https://docs.microsoft.com/fslogix/configure-cloud-cache-tutorial).

- Active-passive. For active-passive, you can use Azure Site Recovery to replicate your VMs in the secondary region with your domain controllers. If you use Azure Site Recovery, you don't need to register the VMs manually. Instead, the Azure Virtual Desktop agent in the secondary VM will automatically use the latest security token to connect to the service instance closest to it. This will ensure your session host joins the host pool automatically, and the user will only need to reconnect to access their VMs. For this configuration, you can also create a secondary host pool (known as a *hot standby*) in the failover region with all the resources turned off. You can then use a recovery plan in Azure Site Recovery to turn on host pools and create an orchestrated process. You also need to create a new application group in the failover region and assign users to them.

>[!Note]
>To learn more how to replicate your VMs in the secondary region read the following Microsoft Learn module: [Protect your Azure infrastructure with Azure Site Recovery](https://docs.microsoft.com/learn/modules/protect-infrastructure-with-site-recovery/).

### Virtual Network

Region failures impact virtual networks and the services deployed within the virtual networks. You must plan for a virtual network in your secondary region. You can create a virtual network manually and then set up with peering with the primary network. You can also use Azure Site Recovery to set up the virtual network in the failover region and preserve your primary network's settings.

In an Azure Virtual Desktop that is connected with your on-premises network, you should configure the virtual network in the secondary region with connectivity to on-premises network.

### FSLogix profiles and MSIX app attach

You can use Azure NetApp Files as a storage option for FSXlogix profiles and MSIX app attach because they support cross-region replication. Azure Files with Standard performance also support cross-region replication. You can configure the FSLogix agent to support multiple profile locations, which helps ensure availability if there's a failure. If the primary location fails, the FSLogix agent will be replicated as part of the VM Azure Site Recovery. The agent will automatically attempt to use the profile path that points to the secondary region. 

>[!Note]
> Learn how to setup Cross-region replication of Azure NetApp Files by reading the following article: [Cross-region replication of Azure NetApp Files volumes](https://docs.microsoft.com/azure/azure-netapp-files/cross-region-replication-introduction),

For the active-active scenario and if the RTO/RTA are less than a day, we recommend that you use FSLogix profiles to use Cloud Cache. Cloud Cache is a feature of FSLogix that must be specifically enabled and configured and allows you to use multiple remote locations, which are all continually updated during the user session.

### Master images

You should replicate master images in the secondary region after each primary desktop image modification. You can use Azure Shared Image Gallery to share custom images across regions. During a primary region failure, you can use cloned desktop images as sources for creation of the host pools.

>[!Note]
> Read more about Shared Image Galleries by reading the following article: [Shared Image Galleries overview](https://docs.microsoft.com/azure/virtual-machines/shared-image-galleries).

### App dependencies

Applications that are dependent on resources available in the primary region will require the same resources in the secondary location. For example, if some of your applications are connected with SQL backend deployed in one region, make sure to replicate SQL in the secondary location. For SQL Server in Azure VM you can use Azure Site Recovery. For SQL as PaaS, you can use active geo-replication or auto-failover groups. You should include these resources in the overall BCDR plan. Additionally, you should include an Azure Site Recovery plan that can model app dependencies in the protection plan.
