Microsoft 365 includes many familiar services, helping you and your organization be more productive. Take a look at Microsoft 365 cloud services and see how they differ from the familiar on-premises versions.

## Learning objectives

In this module, you will:
- Learn what the core Microsoft 365 services and products do.
- Learn the difference between the Microsoft 365 services and their on-premises counterparts.

## Pre-requisites
- None

Exchange Online is a messaging and collaboration platform for your email, calendar, contact info, and tasks. You can access all of this with Microsoft Outlook, Outlook on the web, or Outlook Mobile. You can access Exchange Online on most devices, including Android, iOS, and Windows 10 devices. 

Here are some features of Exchange Online:

- **Mailboxes and online archives**. Individual users have their own mailboxes. Some plans also include an online archive for additional storage.
- **Calendars**. Each user has a calendar to keep track of upcoming events and to check for conflicts when scheduling meetings with coworkers. If needed, users can delegate access to their calendars to other users, like administrative assistants and teammates. 
- **View and edit Office attachments online**. Users can view and edit Office attachments online in Outlook on the web - even without a locally installed version of Office.
- **Shared mailboxes and resources**. You can use shared mailboxes for groups of users that need to share information in a central mailbox. You can also set up resources and equipment for meeting rooms and bookings. 
- **Message policy and compliance**. Exchange Online offers several message policy and compliance features, including retention policies, message encryption, eDiscovery, data loss prevention, and journaling. 
- **Antispam and anti-malware**. All Exchange Online subscriptions include Exchange Online Protection, which provides configurable antispam and anti-malware scanning.
- **Configurable mail flow**. To support specialized mail flow (hybrid, partner, or third-party service scenarios), you can create inbound and outbound connectors in Microsoft 365. For example, you can create connectors that use additional security settings for mail flow with a business partner. 
- **Mobile and multiplatform access**. Users can use Outlook mailboxes and calendars on Windows and Mac clients by using Messaging Application Programming Interface (MAPI) over HTTPS or Microsoft Graph. Exchange Web Services is still supported, but if you’re updating or creating an app, use Microsoft Graph instead. Outlook on the web supports mailboxes and calendars on almost any platform. Mobile devices can access mailboxes and calendars by using Exchange ActiveSync. 
- **Hybrid deployment**. You can integrate Exchange Online with an on-premises Exchange Server organization by implementing a hybrid deployment. In a hybrid deployment, Exchange Online and the on-premises Exchange organization can share a single namespace for messaging. A hybrid deployment also supports calendar sharing and mailbox moves between Exchange Online and an on-premises Exchange server.

## Compare Exchange Online to Exchange Server

Before you can decide whether Exchange Online is right for your organization, you need to understand the differences between Exchange Online and an on-premises Exchange Server. Some of the key differences are described in the following table:

||Exchange Server|Exchange Online|
|:--------|:---------|:----------|
|**Storage**|Many on-premises deployments of Exchange place relatively low limits on mailbox sizes, such as one or two gigabytes (GB). Bigger mailboxes require more hardware (servers and drives).|Exchange Online supports larger mailboxes of 50 GB or more, depending on your plan.|
|**High availability**|You need to purchase and configure hardware to store multiple mailbox copies and configure load balancing to achieve high availability. For true high availability, you also need an alternate datacenter. |Exchange Online is automatically configured for high availability, with data replicated to multiple datacenters.|
|**Backups**|You need to manage your own Exchange Server backups, but you have complete control over them.| Exchange Online replicates data across multiple servers and datacenters, and you configure retention through single-item recovery and litigation hold. There are no built-in methods for configuring backups.|
|**Automatic integration with other Microsoft 365 features**|n/a|Exchange Online offers additional features such as Microsoft 365 Groups, which integrate multiple Microsoft 365 features together. You can also view and edit Office email attachments.|
|**Access to new features**|Some new features from the cloud might eventually be added to Exchange Server, but they'll always appear first in Exchange Online. |You have access to many features that don't exist in an on-premises Exchange organization.| 
|**Access to mailbox databases and servers**|You have access to the Exchange servers and mailbox databases.|You have no access to the Exchange servers in the Microsoft datacenters. Microsoft manages the servers and mailbox databases in Exchange Online for you.|

## Learn more

When you're done with a link, use the **Back** arrow in your browser to come back to this page.

- [Overview of Microsoft Graph](/graph/overview)
 
