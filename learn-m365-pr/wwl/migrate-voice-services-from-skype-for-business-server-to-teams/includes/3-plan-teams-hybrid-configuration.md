Setting up hybrid connectivity is the first step in moving your on-premises environment to the cloud.

Setting up hybrid connectivity and moving all users to the cloud is required before an organization decommissions its on-premises Skype for Business deployment. Once it has set up hybrid connectivity, it can move its users to the cloud based on its schedule and business need.

Before you can implement a Hybrid configuration between Skype for Business Server and Teams, you need to ensure you fulfill the following prerequisites:

### Infrastructure prerequisites

Check that your organization has:
- A Microsoft 365 tenant with Teams enabled

- Azure Active Directory Connect to synchronize your on-premises directory with Microsoft 365

- Skype for Business Server administrative tools, which are required to move users from on-premises to the cloud.

- These tools must be installed on a server with access to both on-premises deployment and Microsoft 365 services, including Microsoft Teams.

- A shared SIP address space must be enabled, and the organization's on-premises deployment must be configured to use Microsoft 365 as a hosting provider.

### Topology prerequisites

One of the following topology scenarios:

- A **Skype for Business Server 2019** deployment with all servers running **Skype for Business Server 2019**.

- A **Skype for Business Server 2015** deployment with all servers running **Skype for Business Server 2015**.

- A **Lync Server 2013** deployment with all servers running **Lync Server 2013**. However, if hybrid voice connectivity is required, a mixed version topology must be used, as noted below.

- A deployment with a **maximum of two different server versions** as listed below:

- **Skype for Business Server 2015** and **Skype for Business Server 2019**

- **Lync Server 2013** and **Skype for Business Server 2019**

- **Lync Server 2013** and **Skype for Business Server 2015**

If hybrid voice is required in any topology, both the edge server that's selected as the Federation Edge and the pool associated with SIP federation must run Skype for Business 2015 or later. Users can remain on a Lync 2013 Pool if one exists.

> [!NOTE]
> Topologies that include Lync Server 2010 aren't supported for hybrid voice of Teams.

Microsoft supports the following multi-forest hybrid scenarios:

- Resource forest topology

- Multiple deployments of Skype for Business Server in multiple forests.

At any given time, only one on-premises Skype for Business forest can be in hybrid mode (shared SIP address space). All other on-premises Skype for Business forests must remain fully on-premises (and presumably federated with each other). If necessary, these other on-premises organizations can sync to Azure Active Directory with new functionality to disable online SIP domains.

### Network prerequisites

When creating DNS records for hybrid deployments, all Skype for Business external DNS records should point to the on-premises infrastructure.

Additionally, you need to ensure that the DNS resolution described in the following table works in your on-premises deployment. (If you already configured federation for on-premises, then you most likely already have these.)

| **DNS record**| **Resolvable by**| **DNS requirement**|
| :--- | :--- | :--- |
| DNS SRV record for _sipfederationtls._tcp.<sipdomain.com> for all supported SIP domains resolving to Access Edge external IP(s)| Edge server(s)| Enable federated communication in a hybrid configuration. The Edge Server needs to know where to route federated traffic for the SIP domain that is split between on premises and online.Must use strict DNS name matching between the domain in the username and the SRV record.|
| DNS A record(s) for Edge Web Conferencing Service FQDN, e.g., webcon.contoso.com resolving to Web Conferencing Edge external IP(s)| Internal corporate network connected users' computers| Enable online users to present or view content in on-premises hosted meetings. Content includes PowerPoint files, whiteboards, polls, and shared notes.|

Depending on how DNS is configured in your organization, you may need to add these records to the internal hosted DNS zone for the corresponding SIP domain(s) to provide internal DNS resolution to these records.

Computers on your network must be able to perform standard Internet DNS lookups. If these computers can reach standard Internet sites, your network meets this requirement.

Depending on the location of your Microsoft Online Services data center, you must also configure your network firewall devices to accept connections based on wildcard domain names (for example, all traffic from *.outlook.com). If your organization's firewalls do not support wildcard name configurations, you will have to manually determine the IP address ranges that you would like to allow and the specified ports.

## General prerequisites

Both the Teams and Skype for Business Online services require that the correct Active Directory attributes exist and are populated in Azure AD.

If users' identities exist across multiple forests, Azure AD Connect should do the merge. When this guidance is followed, Azure AD Connect will automatically synchronize the correct attributes, provided you do not modify either the Connectors or Sync Rules in Azure AD Connect.

If you don't synchronize from all forests that contain user identities and the Skype for Business Server deployment, you must still ensure the relevant identity and Skype for Business attributes are correctly populated into Azure AD for any user using Teams or Skype for Business (whether on-premises or online) - which will likely require additional on-premises directory synchronization.

In such scenarios, it's the customer's responsibility to ensure proper configuration for populating the attributes into Azure AD. Keep the following in mind:

- Using a non-standard configuration for synchronizing to Azure AD is risky because it could lead to misconfiguration, which could cause data corruption in your online directory.

As products evolve, Microsoft will continue to verify standard synchronization configurations in which all relevant forests are synchronized. Customers with custom synchronization configurations are responsible for ensuring their configurations deliver the correct attributes and values into Azure AD.

