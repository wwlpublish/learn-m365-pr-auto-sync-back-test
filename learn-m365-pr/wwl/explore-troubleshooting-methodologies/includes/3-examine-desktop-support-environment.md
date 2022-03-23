In a corporate support environment, you will encounter three types of networks: workgroups, domains, and cloud-based infrastructure. In all of these environments, end users can share common resources, such as files, folders, and printers. These three environments also provide security measures to secure and protect end users’ personal data, in addition to your organization’s network resources and data, from outside forces. Despite their similarities, there are important differences between workgroups, domains, and cloud-based infrastructure, which this section details.

#### Workgroups

Workgroups, or peer-to-peer networks, are logical groupings of networked computers that share resources. Workgroups are the easiest networks to set up and maintain, but they also are the least secure. Each computer maintains its own local security database, which contains the valid user accounts for signing in to that computer. The user accounts secure the data on each computer, and protect the computer from unwanted access. However, the network is decentralized, which means that no single computer provides centralized security of user accounts for all of the network’s computers.

> [!NOTE]
> You typically would configure workgroups for home networks, small home offices, and small businesses in which the computers are in close proximity to one another and often are connected by using a hub, switch, or router. Larger corporations typically do not use workgroups, because they are not as secure as other network options.

#### Domains

Domains are logical groupings of networked computers that share a common user database. In addition, they manage security centrally on a single server, known as a domain controller, or on a group of servers (domain controllers). A single domain must have one or more domain controllers. These computers provide Active Directory Domain Services (AD DS), helping to secure access to resources, and providing a single point of administration.

Domains are logical groupings which you configure independent of the network’s actual physical structure. Domains can span a building, city, state, country/region, or even the globe. You also can configure them for a small office. You can connect a domain’s computers by DirectAccess, virtual private network (VPN), Ethernet, broadband, satellite, or wireless connections.

> [!NOTE]
> Larger companies and corporations typically configure domains because they are the most secure network option. They also are extensible and offer centralized security and management. Smaller companies generally do not use domains because they are more expensive, and require more attention than workgroups.

#### Cloud-based infrastructure and services

Many organizations choose to implement part or all of their network infrastructure, apps, and services in the cloud. When providing support to your users, you might begin to encounter cloud-based infrastructure and services, if you have not already.

> [!NOTE]
> Some organizations extend to the cloud by using a hybrid model, which means that they shift some elements of their apps and infrastructure to the cloud. For example, in a hybrid Exchange environment, an organization will maintain its on-premises Exchange Server while also using Exchange Online in Microsoft 365.

Microsoft provides a number of cloud-based apps and services, including:

 -  **Microsoft 365**. Microsoft 365 delivers online versions of the Office applications and online business collaboration tools. Creating and managing Microsoft 365 accounts and apps is a common task for tier 1 help-desk staff and a tier 2 EDST.
 -  **Microsoft Azure**. This is a public cloud environment, and it provides a collection of Microsoft cloud services that you can use to build and operate cloud-based apps and information technology (IT) infrastructure.

> [!NOTE]
> A global network of data centers host Azure services. Microsoft technicians manage these data centers 24 hours a day, seven days a week. Azure offers a 99.95 percent availability SLA for computing services.

Azure services allow you to:

 -  Create and operate cloud-based apps when you use a wide range of commonly used tools and frameworks.
 -  Host workloads in the cloud infrastructure that comprise virtual machines and virtual networks.
 -  Integrate cloud services with on-premises infrastructure.
