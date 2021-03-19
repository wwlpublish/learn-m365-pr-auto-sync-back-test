If you have on-premises Skype for Business users who are simultaneously using Microsoft Teams, they cannot inter-operate with Skype for Business users from their Teams client, nor can they communicate with users in federated organizations from their Teams client. If these users want to add this functionality in Teams, you must complete the following tasks:

 *  The users must be moved from on-premises Skype for Business to the cloud, which requires configuring a hybrid Skype for Business deployment.
 *  You must upgrade to Teams Only mode in the Microsoft Teams admin center.

You can upgrade either individual users or the entire tenant to Teams Only mode. Upgrading to Teams Only mode maximizes the user experience by offering users the full benefits of Microsoft Teams, the hub for teamwork in Microsoft 365, through a single client experience. Users in Teams Only mode will receive all calls and chats in Teams, regardless of whether the sender is using Skype for Business or Teams. Operating in Teams Only mode also solves the initial problem mentioned at the start of this unit. On-premises Skype for Business users who are simultaneously using Microsoft Teams can now inter-operate with Skype for Business users from their Teams client, and they can communicate with users in federated organizations from their Teams client.

Setting up hybrid connectivity and moving all users to the cloud is required before you decommission your on-premises Skype for Business deployment. Once you have set up hybrid connectivity, you can move your users to the cloud based on your schedule and business need. With Direct Routing, you can use your on-premises voice infrastructure while you move to the cloud and after your migration is complete. This type of deployment is sometimes referred to as "split domain," which means that users of a domain, such as contoso.com, are split between using on-premises Skype for Business Server and Skype for Business Online. This configuration has the following effect on users:<br>

 *  Users who are homed on-premises can interact with on-premises Skype for Business servers.
 *  Users who are homed online can interact with Skype for Business online services.
 *  Users from both environments can collaborate with each other by using Instant Messaging, participating in conference calls, VoIP calls, and so on.
 *  Azure Active Directory Connect is used to synchronize the organization’s on-premises directory with Microsoft 365.

The following diagram shows a Skype for Business "split domain" hybrid configuration. Users A and B are homed online but are discoverable by on-premises users; whereas, users C and D are homed on-premises but are discoverable by online users.

:::image type="content" source="../media/hybrid-skype-for-business-deployment-2419c5f5.png" alt-text="diagram shows a Skype for Business split domain hybrid configuration":::


### Infrastructure requirements

Organizations must consider the following infrastructure requirements when planning a Skype for Business hybrid deployment:

 *  A single on-premises deployment of Skype for Business Server or Lync Server that is deployed in a supported topology. See the next section on Topology requirements.
 *  A Microsoft 365 tenant with Skype for Business Online enabled.
 *  Azure Active Directory Connect to synchronize your on-premises directory with Microsoft 365. For more information, see [Azure AD Connect: Accounts and permissions](https://aka.ms/AA4jz5u?azure-portal=true).
 *  Skype for Business Server administrative tools, which are required to move users from on-premises to the cloud. These tools must be installed on a server with access to both on-premises deployment and the internet.
 *  The Teams admin center or Windows PowerShell can be used to manage Teams and Skype for Business Online. To use PowerShell to manage either Teams or Skype for Business Online, download and install the [Skype for Business Online Connector](https://aka.ms/AA4jz6e?azure-portal=true).
 *  Shared SIP address space must be enabled, and your on-premises deployment must be configured to use Microsoft 365 as a hosting provider. For more information about the steps required to configure hybrid connectivity, see [Configure hybrid connectivity between Skype for Business Server and Microsoft 365](https://aka.ms/AA4jz5w?azure-portal=true).

### Topology requirements

Organizations must implement one of the following topology scenarios when configuring a Skype for Business hybrid deployment:

 *  A Skype for Business Server 2019 deployment with all servers running Skype for Business Server 2019.
 *  A Skype for Business Server 2015 deployment with all servers running Skype for Business Server 2015.
 *  A Lync Server 2013 deployment with all servers running Lync Server 2013. However, if hybrid voice connectivity is required, you must use a mixed version topology as noted below.
 *  A deployment with a maximum of two different server versions as listed below:
    
     *  Skype for Business Server 2015 and Skype for Business Server 2019
     *  Lync Server 2013 and Skype for Business Server 2019
     *  Lync Server 2013 and Skype for Business Server 2015

If hybrid voice is desired in any topology, both the edge server that is designated as the Federation Edge and the pool associated with SIP federation must run Skype for Business 2015 or later. Users can remain on a Lync 2013 Pool if one exists. For more information, see [Plan Phone System in Office 365 with on-premises PSTN Connectivity in Skype for Business Server](https://aka.ms/AA4jz6m?azure-portal=true).

Topologies that include Lync Server 2010 are not supported for hybrid voice or Teams. The following topologies that include Lync Server 2010 are supported with Skype for Business Online for instant messaging and meetings:

 *  A mixed Lync Server 2010 and Skype for Business Server 2015 deployment
 *  A mixed Lync Server 2010 and Lync Server 2013 deployment
 *  A Lync Server 2010 deployment with all servers running Lync Server 2010 with the latest cumulative updates

### Multi-forest support

Microsoft supports the following multi-forest hybrid scenarios:

 *  **Resource forest topology.** In this kind of topology, there is one forest that hosts Skype for Business Server (the resource forest), and there are one or more other forests that host account identities, which access the Skype for Business Server in the resource forest. In general, users can access Skype for Business functionality in another forest if the following requirements are met:
    
     *  Users are properly synchronized into the forest that hosts Skype for Business. In hybrid configurations, users must be synchronized as disabled user objects.
     *  The forest hosting Skype for Business must trust the forest containing the users. For details on resource forest hybrid scenarios, see [Deploy a resource forest topology](https://aka.ms/AA4jrtp?azure-portal=true).
 *  **Multiple deployments of Skype for Business Server in multiple forests**. This configuration can be found in more complex enterprises, and in deployments that are the result of mergers and acquisitions. Consolidation of all users from on-premises to the cloud in a single Microsoft 365 tenant can be achieved for any organization with multiple Skype for Business deployments when the following key requirements are met:
    
     *  There cannot be more than one Microsoft 365 tenant involved. Consolidation in scenarios with more than one Microsoft 365 tenant is not supported.
     *  At any given time, only one on-premises Skype for Business forest can be in hybrid mode (shared SIP address space). All other on-premises Skype for Business forests must remain fully on-premises (and presumably federated with each other). These other on-premises organizations can sync to Azure Active Directory if desired with new functionality to disable online SIP domains available as of December 2018.

Customers with deployments of Skype for Business in multiple forests must first fully migrate each Skype for Business forest individually into the Microsoft 365 tenant using split-domain (Shared SIP Address Space) functionality. Once that is complete, they can then disable hybrid with the on-premises deployment, and then move on to migrate the next on-premises Skype for Business deployment.

> ![Note]
> Prior to being migrated to the cloud, on-premises users remain in a federated state with any users that are not represented in the same user’s on-premises directory. For more information, see [Cloud consolidation for Teams and Skype for Business](https://aka.ms/AA4jrup?azure-portal=true).

### Port and protocol requirements

In addition to the port requirements for internal communication, you must also configure the following ports to enable hybrid connectivity:

    | <b>Protocol</b> | <b>TCP or UDP</b> | <b>Source IP</b> | <b>Destination IP</b> | <b>Source Port</b> | <b>Destination Port</b> | <b>Notes</b>                                        |
    |:----------------------:|:------------------------:|:-----------------------:|:----------------------------:|:-------------------------:|:------------------------------:|:---------------------------------------------------------- |
    |   SIP (MTLS)    |        TCP        |   Access Edge    |     Microsoft 365     |        Any         |          5061           | Signaling                                           |
    |   SIP (MTLS)    |        TCP        |  Microsoft 365   |      Access Edge      |        Any         |          5061           | Signaling                                           |
    |      STUN       |        TCP        |     A/V Edge     |     Microsoft 365     |    50000-59999     |           443           | Open for audio, video, application sharing sessions |
    |      STUN       |        TCP        |  Microsoft 365   |       A/V Edge        |    50000-59999     |           443           | Open for audio, video, application sharing sessions |
    |      STUN       |        UDP        |     A/V Edge     |     Microsoft 365     |        3478        |          3478           | Open for audio, video sessions                      |
    |      STUN       |        UDP        |  Microsoft 365   |       A/V Edge        |        3478        |          3478           | Open for audio, video sessions                      |
