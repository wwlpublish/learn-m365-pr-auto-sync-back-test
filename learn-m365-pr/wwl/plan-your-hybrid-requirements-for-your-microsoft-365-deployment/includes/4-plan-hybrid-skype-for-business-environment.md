<br>When an organization has on-premises Skype for Business users who are simultaneously using Microsoft Teams, they can't inter-operate with Skype for Business users from their Teams client. They also can't communicate with users in federated organizations from their Teams client. If these users want to add this functionality in Teams, the organization must complete the following tasks:

 -  Move the users from on-premises Skype for Business to the cloud, which requires configuring a hybrid Skype for Business deployment.
 -  Upgrade to Teams Only mode in the Microsoft Teams admin center.

An organization can upgrade either individual users or its entire tenant to Teams Only mode. Upgrading to Teams Only mode maximizes the user experience by offering users the full benefits of Microsoft Teams, the hub for teamwork in Microsoft 365, through a single client experience. Users in Teams Only mode will receive all calls and chats in Teams, regardless of whether the sender is using Skype for Business or Teams. Operating in Teams Only mode also solves the initial problem mentioned at the start of this unit. On-premises Skype for Business users who are simultaneously using Microsoft Teams can now inter-operate with Skype for Business users from their Teams client. They can also communicate with users in federated organizations from their Teams client.

Setting up hybrid connectivity and moving all users to the cloud is required before an organization decommissions its on-premises Skype for Business deployment. Once it has set up hybrid connectivity, it can move its users to the cloud based on its schedule and business need.

With Direct Routing, an organization can use its on-premises voice infrastructure while it moves to the cloud and after its migration is complete. This type of deployment is sometimes referred to as "split domain," which means that users of a domain, such as contoso.com, are split between using on-premises Skype for Business Server and Skype for Business Online. This configuration has the following effect on users:<br>

 -  Users who are homed on-premises can interact with on-premises Skype for Business servers.
 -  Users who are homed online can interact with Skype for Business online services.
 -  Users from both environments can collaborate with each other by using Instant Messaging, participating in conference calls, VoIP calls, and so on.
 -  Azure Active Directory Connect is used to synchronize the organization’s on-premises directory with Microsoft 365.

The following diagram shows a Skype for Business "split domain" hybrid configuration. Users A and B are homed online but are discoverable by on-premises users. Users C and D are homed on-premises but are discoverable by online users.

:::image type="content" source="../media/hybrid-skype-for-business-deployment-2419c5f5.png" alt-text="diagram shows a Skype for Business split domain hybrid configuration":::


### Infrastructure requirements

Organizations must consider the following infrastructure requirements when planning a Skype for Business hybrid deployment:

 -  A single on-premises deployment of Skype for Business Server or Lync Server that's deployed in a supported topology. See the next section on Topology requirements.
 -  A Microsoft 365 tenant with Skype for Business Online enabled.
 -  Azure Active Directory Connect to synchronize your on-premises directory with Microsoft 365. For more information, see [Azure AD Connect: Accounts and permissions](/azure/active-directory/hybrid/reference-connect-accounts-permissions?azure-portal=true).
 -  Skype for Business Server administrative tools, which are required to move users from on-premises to the cloud. These tools must be installed on a server with access to both on-premises deployment and the internet.
 -  The Teams admin center or Windows PowerShell can be used to manage Teams and Skype for Business Online. To use PowerShell to manage either Teams, see [Install Microsoft Teams PowerShell Module](/microsoftteams/teams-powershell-install?azure-portal=true).
 -  Shared SIP address space must be enabled, and the organization's on-premises deployment must be configured to use Microsoft 365 as a hosting provider. For more information about the steps required to configure hybrid connectivity, see [Configure hybrid connectivity between Skype for Business Server and Teams](/skypeforbusiness/hybrid/configure-hybrid-connectivity?azure-portal=true).

### Topology requirements

Organizations must implement one of the following topology scenarios when configuring a Skype for Business hybrid deployment:

 -  A Skype for Business Server 2019 deployment with all servers running Skype for Business Server 2019.
 -  A Skype for Business Server 2015 deployment with all servers running Skype for Business Server 2015.
 -  A Lync Server 2013 deployment with all servers running Lync Server 2013. However, if hybrid voice connectivity is required, a mixed version topology must be used, as noted below.
 -  A deployment with a maximum of two different server versions as listed below:
    
     -  Skype for Business Server 2015 and Skype for Business Server 2019
     -  Lync Server 2013 and Skype for Business Server 2019
     -  Lync Server 2013 and Skype for Business Server 2015

If hybrid voice is required in any topology, both the edge server that's selected as the Federation Edge and the pool associated with SIP federation must run Skype for Business 2015 or later. Users can remain on a Lync 2013 Pool if one exists. For more information, see [Plan Phone System in Office 365 with on-premises PSTN Connectivity in Skype for Business Server](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-phone-system-with-on-premises-pstn-connectivity?azure-portal=true).

Topologies that include Lync Server 2010 aren't supported for hybrid voice or Teams. The following topologies that include Lync Server 2010 are supported with Skype for Business Online for instant messaging and meetings:

 -  A mixed Lync Server 2010 and Skype for Business Server 2015 deployment.
 -  A mixed Lync Server 2010 and Lync Server 2013 deployment.
 -  A Lync Server 2010 deployment with all servers running Lync Server 2010 with the latest cumulative updates.

### Multi-forest support

Microsoft supports the following multi-forest hybrid scenarios:

 -  **Resource forest topology.** In this kind of topology, there's one forest that hosts Skype for Business Server (the resource forest), and there are one or more other forests that host account identities. These identities access the Skype for Business Server in the resource forest. In general, users can access Skype for Business functionality in another forest if the following requirements are met:
    
     -  Users are properly synchronized into the forest that hosts Skype for Business. In hybrid configurations, users must be synchronized as disabled user objects.
     -  The forest hosting Skype for Business must trust the forest containing the users. For details on resource forest hybrid scenarios, see [Deploy a resource forest topology](https://docs.microsoft.com/skypeforbusiness/hybrid/configure-a-multi-forest-environment-for-hybrid#:~:text=%20Deploy%20a%20resource%20forest%20topology%20%201,the%20resource%20forests%20hosting%20Skype%20for...%20More%20?azure-portal=true).
 -  **Multiple deployments of Skype for Business Server in multiple forests**. This configuration can be found in more complex enterprises, and in deployments that are the result of mergers and acquisitions. Consolidation of all users from on-premises to the cloud in a single Microsoft 365 tenant can be achieved for any organization with multiple Skype for Business deployments when the following key requirements are met:
    
     -  There can't be more than one Microsoft 365 tenant involved. Consolidation in scenarios with more than one Microsoft 365 tenant isn't supported.
     -  At any given time, only one on-premises Skype for Business forest can be in hybrid mode (shared SIP address space). All other on-premises Skype for Business forests must remain fully on-premises (and presumably federated with each other). If necessary, these other on-premises organizations can sync to Azure Active Directory with new functionality to disable online SIP domains.

Customers with deployments of Skype for Business in multiple forests must first fully migrate each Skype for Business forest individually into the Microsoft 365 tenant using split-domain (Shared SIP Address Space) functionality. Once that is complete, they can then disable hybrid with the on-premises deployment, and then move on to migrate the next on-premises Skype for Business deployment.

Before they're migrated to the cloud, on-premises users remain in a federated state with any users that aren't represented in the same user’s on-premises directory. For more information, see [Cloud consolidation for Teams and Skype for Business](/skypeforbusiness/hybrid/cloud-consolidation?azure-portal=true).

### Port and protocol requirements

Besides the port requirements for internal communication, an organization must also configure the following ports to enable hybrid connectivity:

:::row:::
  :::column:::
    **Protocol**
  :::column-end:::
  :::column:::
    **TCP or UDP**
  :::column-end:::
  :::column:::
    **Source IP**
  :::column-end:::
  :::column:::
    **Destination IP**
  :::column-end:::
  :::column:::
    **Source Port**
  :::column-end:::
  :::column:::
    **Destination Port**
  :::column-end:::
  :::column:::
    **Notes**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    SIP (MTLS)
  :::column-end:::
  :::column:::
    TCP
  :::column-end:::
  :::column:::
    Access Edge
  :::column-end:::
  :::column:::
    Microsoft 365
  :::column-end:::
  :::column:::
    Any
  :::column-end:::
  :::column:::
    5061
  :::column-end:::
  :::column:::
    Signaling
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    SIP (MTLS)
  :::column-end:::
  :::column:::
    TCP
  :::column-end:::
  :::column:::
    Microsoft 365
  :::column-end:::
  :::column:::
    Access Edge
  :::column-end:::
  :::column:::
    Any
  :::column-end:::
  :::column:::
    5061
  :::column-end:::
  :::column:::
    Signaling
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    STUN
  :::column-end:::
  :::column:::
    TCP
  :::column-end:::
  :::column:::
    A/V Edge
  :::column-end:::
  :::column:::
    Microsoft 365
  :::column-end:::
  :::column:::
    50000-59999
  :::column-end:::
  :::column:::
    443
  :::column-end:::
  :::column:::
    Open for audio, video, application sharing sessions
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    STUN
  :::column-end:::
  :::column:::
    TCP
  :::column-end:::
  :::column:::
    Microsoft 365
  :::column-end:::
  :::column:::
    A/V Edge
  :::column-end:::
  :::column:::
    50000-59999
  :::column-end:::
  :::column:::
    443
  :::column-end:::
  :::column:::
    Open for audio, video, application sharing sessions
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    STUN
  :::column-end:::
  :::column:::
    UDP
  :::column-end:::
  :::column:::
    A/V Edge
  :::column-end:::
  :::column:::
    Microsoft 365
  :::column-end:::
  :::column:::
    3478
  :::column-end:::
  :::column:::
    3478
  :::column-end:::
  :::column:::
    Open for audio, video sessions
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    STUN
  :::column-end:::
  :::column:::
    UDP
  :::column-end:::
  :::column:::
    Microsoft 365
  :::column-end:::
  :::column:::
    A/V Edge
  :::column-end:::
  :::column:::
    3478
  :::column-end:::
  :::column:::
    3478
  :::column-end:::
  :::column:::
    Open for audio, video sessions
  :::column-end:::
:::row-end:::
