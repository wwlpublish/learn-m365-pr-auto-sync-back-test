Resiliency is another key design principle for Microsoft 365 architecture and service design. Microsoft designs and builds our cloud services to maximize reliability and minimize the negative effects on customers in the face of faults and challenges to normal operations. Rather than relying on traditional resilience strategies involving complex physical infrastructure, Microsoft builds redundancy directly into online services. We combine redundant infrastructure with intelligent software to maximize data resiliency, avoid downtime, and meet our 99.9% availability SLA.

## Service resiliency

Microsoft 365's resilience strategy prioritizes software resiliency. This means that we focus on building resiliency into the design of our services, protecting against service downtime regardless of failures in underlying hardware. Service resiliency allows our services to automatically recover from many kinds of faults and failures without impacting service availability.

Microsoft 365 services implement a number of resiliency principles, including:

- **Active/Active service design:** Wherever possible, we ensure our services are designed and deployed with Active/Active resiliency. This means that if a critical component of the service fails, an identical component is available to take over without a loss of availability.
- **Fault isolation:** Fault isolation increases service resilience by preventing faults in one component from causing other components to fail. Microsoft 365 works continuously to reduce the size of fault zones in our services to prevent failures from spreading and impacting other system components. For example, Exchange Online Database Availability Groups limit the impact of failures within the service to specific availability groups.
- **Monitoring and self-healing:** Microsoft 365 services employ a variety of automated mechanisms that continuously monitor the health of our services and route traffic to optimal service clusters. Many of our services include self-healing mechanisms when an issue is detected. For example, Exchange Online automatically restores mailbox databases if it detects a disk failure that impacts an availability group.

## Data resiliency

Data resiliency complements service resiliency by protecting the integrity and availability of data in Microsoft 365 services. Microsoft 365 data resiliency focuses on ensuring that critical customer data remains available and unmodified in the face of unexpected faults and failures. To achieve this, Microsoft 365 services implement the following data resiliency principles:

- **Data criticality:** Our services are designed to protect critical customer data. To accomplish this, we categorize data processed by our systems as either critical or non-critical. Non-critical data, such as whether a message was read, can be dropped in rare failure scenarios. Critical data, such as customer data, is protected against loss during failure scenarios.
- **Data redundancy:** Our services use local storage redundancy and geo-redundancy to replicate copies of customer data into different fault zones. If data is corrupted or lost in one fault zone, it can be accessed in another fault zone without loss of availability.
- **Granular monitoring and automated recovery:** Our systems monitor customer data integrity and automatically restore corrupted data. For example, Exchange Online monitors for data corruption at multiple levels and automatically restores databases or mailboxes that experience corruption.
- **Protection against accidental loss:** Most data loss results from customer actions. Microsoft 365 provides customers with tools to recover accidentally deleted or modified data in Exchange Online and SharePoint Online.

## Network  resiliency

Microsoft owns and operates one of the largest backbone networks in the world, connecting hundreds of datacenters in 54 global regions. Our network is supported by hundreds of thousands of kilometers of Private Fiber to provide near perfect availability, high capacity, and network flexibility around the world.

Our network of Microsoft datacenters is designed with proximity to our customers in mind and utilizes hundreds of edge nodes to maintain service availability. The network architecture includes direct interconnections and multiple network paths. Our services leverage this redundancy to automatically route traffic around failures to improve service quality. In addition, our network gives us direct control of network capacity, and we use Software Defined Networking to proactively manage network traffic at scale to maximize performance and resilience.

## Shared responsibilities and dependencies

In cloud environments, resiliency is a shared responsibility between the cloud provider and the customer. While Microsoft 365 focuses on the resiliency of its services and network, customers need to be aware of their responsibilities and dependencies for ensuring the availability of the services.

Customer responsibilities for resilience vary based on the specific Microsoft 365 product and the specific customer configuration, but they often include:

- Maintaining licenses for Microsoft 365 subscriptions.
- Maintaining adequate network connectivity from end-user devices.
- Training users to understand retention and recovery policies and to use retention features.
- Initiating data recovery within the service retention times for relevant services.
- Managing and maintaining any on-premises directories.
- Reviewing and resolving Azure AD sync errors.
- Developing and adopting contingency policies (for example, setting up emergency admin access accounts).
- Managing and ensuring connectivity and functionality of customer HSMs

## Learn more

- [Microsoft 365 Monitoring and Self-Healing](/compliance/assurance/assurance-monitoring-and-self-healing?azure-portal=true)
- [Built in resiliency](/compliance/assurance/assurance-m365-service-resiliency?azure-portal=true)
- [Data Resiliency in Microsoft 365](/compliance/assurance/assurance-data-resiliency-overview?azure-portal=true)
- [Dealing with Data Corruption in Microsoft 365](/compliance/assurance/assurance-dealing-with-data-corruption?azure-portal=true)
- [Exchange Online Data Resiliency in Microsoft 365](/compliance/assurance/assurance-exchange-data-resiliency?azure-portal=true)
- [SharePoint and OneDrive data resiliency in Microsoft 365](/compliance/assurance/assurance-sharepoint-onedrive-data-resiliency?azure-portal=true)
