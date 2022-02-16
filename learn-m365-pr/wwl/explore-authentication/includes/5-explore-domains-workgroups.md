Domains and workgroups provide a method for sharing and accessing resources on a network, such as access to files and printers on other devices in the network.

### What is a Workgroup?

During installation, Windows creates a default Workgroup called “WORKGROUP”. A Workgroup can share files, network storage, printers, and any connected resource. There's no centralization of user accounts and related security policies and settings. It's a peer-to-peer network, in which each device has its own set of user and group accounts, its own security policy, and its own resources that you can share with others.

The workgroup name can be changed by opening the **Control Panel**, selecting **System and Security**, then **System** and selecting **Change settings**.

Workgroups include the following attributes:

 -  All computers have equal rights.
 -  Can’t be password protected.
 -  Has a limit of 20 computers.
 -  All computers must be on same local network.
 -  Works on all Windows versions.
 -  Works on both IP versions: IPv4 and IPv6.
 -  Every computer must have the same workgroup name to communicate.
 -  Requires security and sharing permissions to be set.

You must set up user accounts on each computer. This step is necessary because there's no centralization of user accounts in a workgroup. When users map a network drive to a folder that you've shared on your computer, they must provide credentials to connect to the resource; the sharing computer stores these credentials.

### What is a Domain?

Active Directory and Azure Active Directory Domain Services domains are also a collection of resource-sharing computers with the following characteristics:

 -  **A domain is an administrative boundary**. All domains host an Administrator user account that has full administrative capabilities over all objects within the domain. Although the administrator can delegate administration on objects within the domain, the account retains full administrative control of all objects within the domain.
 -  **A domain is a replication boundary**. If AD DS, it consists of three elements, or partitions: the schema, the configuration partition, and the domain partition. Generally, it's only the domain partition that changes frequently. The domain partition contains objects that are likely to be updated often; these include users, computers, groups, and organizational units (OUs). AD DS replication updates objects and synchronizes information between domain controllers.

If Azure AD, it's hosted in the cloud. Replicas of the Azure AD architecture are synchronized between Microsoft Datacenters, which is transparent to the customer. When using AD DS and Azure AD together, Azure AD Connect synchronizes information between the two environments.

 -  **A domain is an authentication boundary**. Domain controllers from each domain or the Azure AD service can authenticate each user account in that domain. Domains in an AD DS forest trust one another, and it's these trusts that enable a user from one domain to access resources held in another domain.

You can add a computer by joining it to a domain. The computer can belong to one domain only. A computer can belong to a domain or a workgroup, but not both.

The most significant benefit of adding a computer to an AD DS domain is that users can enjoy access to resources throughout the AD DS forest, assuming that they have the necessary permissions. They can do this without needing to remember multiple user accounts and passwords. The major benefit for the administrator is that the domain provides a single store for user and group accounts, a domain-wide security policy, and the ability to configure and manage domain-joined computers from a single point.

> [!NOTE]
> Before you can add a computer to a domain, the computer must be able to locate a domain controller or be connected to the internet to access the Azure AD service. This requires proper configuration of the computer’s name resolution settings.
