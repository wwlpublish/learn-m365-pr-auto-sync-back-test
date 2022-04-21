Microsoft 365 provides a range of migration options that organizations must consider before moving their email data to Exchange Online. These options involve both migration and coexistence strategies. It's important to understand the difference between them.

 -  **Migration.** Migration is the process of moving user data from a source messaging system to Exchange Online. In a migration scenario, an organization wants to move its existing mailboxes to Exchange Online as quickly as possible, without the need to maintain a long-term coexistence.
 -  **Coexistence.** Coexistence is another term for a fully hybrid environment. It's the process of maintaining an organization's existing on-premises messaging system and Exchange Online at the same time. Unlike migration, coexistence enables an organization to move mailboxes between its on-premises mail servers and Exchange Online without its users noticing a difference. As such, coexistence provides the smoothest way to move mailboxes from the user perspective, but it also requires the most work for mail administrators.
    
    With coexistence, on-premises server products are synchronized or integrated to cloud enterprise services. In this state, an organization can either pool resources to one location or have a mixed bag of resources located on-premises and in the cloud. For example, an organization could integrate its on-premises Exchange environment with Exchange Online. In doing so, it may need to keep some mailboxes local to its environment for proprietary purposes. However, it may have many mailboxes located in the cloud for ease of use and backup purposes.

An organization can migrate mailboxes from an Exchange Server or from another email system.

### Migrate from an on-premises Exchange Server environment

An organization can migrate the following user mailbox items from its existing on-premises Exchange Server environment to Microsoft 365:

 -  email
 -  calendar items
 -  tasks
 -  contacts

The following sections outline the types of migrations that can be used when migrating from an Exchange Server environment.

#### Cutover migration

An organization should consider a cutover migration if it plans to migrate all its on-premises mailboxes to Microsoft 365 over a few days. The mail contacts and distribution groups in the on-premises Exchange organization are also migrated.

Cutover migrations are available for organizations:

 -  running Exchange 2003 or Exchange 2007
 -  with fewer than 2000 mailboxes
 -  who want to move mailboxes all at one time

> [!NOTE]
> A cutover migration supports moving up to 2000 mailboxes. However, due to length of time it takes to create and migrate 2000 users, it's more reasonable to migrate 150 users or fewer.

After the migration is complete, each user who has an on-premises Exchange mailbox also will be a new user in Microsoft 365. However, the migration doesn't assign a Microsoft 365 or Office 365 license to each user. You must still assign licenses to users whose mailboxes are migrated.

**Additional reading**. For more information on cutover migrations, see [Migrate email to Exchange Online using the Exchange cutover method](/exchange/mailbox-migration/cutover-migration-to-office-365).

#### Staged migration

An organization should consider a staged migration if it plans to eventually migrate all its on-premises mailboxes to Microsoft 365. A staged migration migrates batches of on-premises mailboxes to Microsoft 365 over the course of a few weeks or months.

Staged migrations are available for organizations:

 -  running Exchange 2003 or Exchange 2007
 -  with more than 2000 mailboxes
 -  who want to move mailboxes over in batches over a period of weeks or months

With staged migrations, you must complete a one-time Active Directory synchronization with Microsoft 365. The purpose of the synchronization is to create recipients in Microsoft 365. When that's complete, you can select batches of mailboxes to move to Microsoft 365. A staged migration migrates a batch of users at a time. You must begin by identifying the users whose on-premises mailboxes you want to migrate to Microsoft 365. After grouping the users in batches, you must create a comma-separated value (CSV) file for each batch of users. Each row in the CSV file contains information about an on-premises mailbox.

> [!NOTE]
> There isn't a limit for the number of mailboxes that you can migrate to Microsoft 365 using a staged migration. The CSV file for a migration batch can contain a maximum of 2,000 rows. To migrate more than 2,000 mailboxes, create more CSV files and use each file to create a new migration batch.

During the migration, the Simple Mail Transfer Protocol (SMTP) address of each on-premises mailbox is used to create the email address for a new Microsoft 365 mailbox. To run a staged migration, the on-premises domain must be verified as a domain you own in your Microsoft 365 organization.

Once an organization has run a staged migration, the users who were migrated are provided with new sign-in credentials. They must then reconfigure their Outlook and other mail app profiles. The organization must license the users after they're created in the staged migration. You have 30 days to add licenses after the users are created.

**Additional reading**. For more information on staged migrations, see [Perform a staged migration of email in Exchange Online](/exchange/mailbox-migration/perform-a-staged-migration/perform-a-staged-migration).

#### Exchange Hybrid migration

An Exchange Hybrid deployment offers organizations the ability to extend the feature-rich experience and administrative control they have with their existing on-premises Microsoft Exchange organization to the cloud. A hybrid deployment provides the seamless look and feel of a single Exchange organization between an on-premises Exchange organization and Exchange Online. In addition, a hybrid deployment can serve as an intermediate step to moving completely to an Exchange Online organization.

In an Exchange hybrid deployment, there are three different types of hybrid migration options:

 -  **Full hybrid migration**. This migration type is best for large organizations that have several thousand mailboxes and need complete integration between their on-premises Exchange organization and Microsoft 365. Active Directory is synchronized with Microsoft 365, free/busy information can be exchanged, enhanced mail flow options become available, and more.
 -  **Minimal hybrid migration**. This migration type is best for medium-sized organizations that have a few hundred to a couple thousand mailboxes and want to finish their migration within a couple months. Like full hybrid, minimal hybrid migrations set up on-going Active Directory synchronization with Microsoft 365 to help with recipient administration. However, features like free/busy synchronization and other enhanced features aren't available.
 -  **Express migration**. This migration type is best for small organizations that want to finish their migration within a couple weeks. Express migration does a one-time Active Directory synchronization with Microsoft 365 to set up recipients. It then helps move their mailboxes to Microsoft 365. No enhanced features are available.

The Hybrid Configuration Wizard (HCW) supports both Classic and Modern hybrid topologies.

 -  **Classic Hybrid topology**. Classic Hybrid requires that internal Exchange servers are accessible from Exchange Online through the HTTPS protocol. This connection allows Exchange Online to connect to the internal Exchange organization for hybrid capabilities. Publishing your internal Exchange Servers to the Internet requires a dedicated public IP address and an official TLS certificate. The Classic Hybrid topology includes:
    
     -  Classic Full
     -  Classic Minimal
     -  Classic Express
 -  **Modern Hybrid topology**. Modern Hybrid doesn't require any inbound HTTPS connection from Exchange Online to the internal Exchange organization. Instead, the Exchange Hybrid Agent connects the on-premises Exchange organization and Exchange Online. This agent is installed on a server and runs as a service that connects to Exchange Online using an outbound HTTPS connection. The Hybrid Agent supports free/busy requests from Exchange Online to the on-premises Exchange server and mailbox migrations.
    
    In a hybrid Exchange deployment, Modern Hybrid is the preferred option because you don't have to install extra components for incoming HTTPS connections. However, if your organization uses Microsoft Teams, you can't use this option if you want the Microsoft Teams users to continue to use their mailboxes in the company's on-premises Exchange servers. In this case, the Classic Full hybrid option is the company's only choice. The Modern Hybrid topology includes:
    
     -  Modern Full
     -  Modern Minimal

The Classic Hybrid topology provides organizations with more flexibility than the Modern Hybrid topology. However, that flexibility comes at a price, since Classic Hybrid has far more setup and operational requirements than Modern Hybrid. The advantage that Modern Hybrid migrations provide is they can be completed more quickly than Classic Hybrid migrations. This feature, in turn, enables organizations to get their Exchange hybrid deployments up and running more quickly.

The following table compares the options available in the Classic Hybrid topology and Modern Hybrid topology.

> [!NOTE]
> This table is an expanded version of the one that was originally published in Chapter 13 in the book, Microsoft Office 365 Administration Inside Out, 2nd Edition. Reference- Fisher, Ed; Guilmette, Aaron; Kegg, Darryl; Mandich, Lou. Microsoft Office 365 Administration Inside Out (Includes Current Book Service), 2nd ed. Pearson Education, Inc., 2017. Print.

:::row:::
  :::column:::
    **Exchange Hybrid Configuration Options**
  :::column-end:::
  :::column:::
    **Classic Minimal**
  :::column-end:::
  :::column:::
    **Classic Express**
  :::column-end:::
  :::column:::
    **Classic Full**
  :::column-end:::
  :::column:::
    **Modern Minimal**
  :::column-end:::
  :::column:::
    **Modern Full**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    E-mail Address Policy and Domain configuration
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Send and Receive Connector Configuration
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    OAuth Configuration
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes for Exchange 2013/2016/2019 with current CU
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes for Exchange 2013/2016/2019 with current CU
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Federation Trust and Organization Relationship
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    MRS Endpoint Configuration
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Azure AD Connect in Express Configuration
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    No; set up separately
  :::column-end:::
  :::column:::
    No; set up separately
  :::column-end:::
  :::column:::
    No; set up separately
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Organization Configuration Transfer
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Hybrid Modern Authentication
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No; the HCW provides the foundational components to prepare the environment for Hybrid Modern Authentication.
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Cross-premises multi mailbox search
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Cross-premises Mail Tips
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Autodiscover external DNS and a public certificate required
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes (see note after the table)
  :::column-end:::
  :::column:::
    Yes (see note after the table)
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Transport external DNS and public certificate required
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Exchange Web Services (EWS) external DNS and public certificate required
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    TCP Port 443 Inbound to Exchange On-premises
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes for Autodiscover if needed; No for Hybrid Agent
  :::column-end:::
  :::column:::
    Yes for Autodiscover if needed; No for Hybrid Agent
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    TCP Port 443 Outbound to Exchange Online
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    TCP Port 25 Inbound to Exchange on-premises
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    TCP Port 25 Outbound to Exchange Online Protection
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    TCP Port 80 Outbound for Certificate Revocation Check
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Third-Party Certificate Required- Autodiscover/Transport/EWS for Exchange On-Premises, Exchange Server 2013/2016/2019
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes for Autodiscover if needed; No for Hybrid Agent
  :::column-end:::
  :::column:::
    Yes for Autodiscover and Transport if needed; No for Hybrid Agent
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Exchange Server Edge 2013/2016/2019 with Edge Sync and Edge Third-Party Certificate for Transport Option, TCP Port 25 in/out at network egress
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Exchange Server Edge 2013/2016/2019 without Edge Sync and Edge Third-Party Certificate for Transport Option, TCP Port 25 in/out at network egress
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
:::row-end:::


> [!NOTE]
> Depending on your topology and configuration, you may still need to publish Autodiscover records in external DNS. You may also need to open TCP Port 25 inbound and outbound to your Exchange environments. These tasks may be needed for other reasons. For example, Exchange Active Sync Clients using the legacy mail client in Android or iOS. That being said, it's highly recommended that organizations use Microsoft Outlook for iOS and Android as the mobile messaging application. Another reason may be using a feature like Exchange Server Hybrid Modern Authentication. For more information, review the limitations of the hybrid agent and modern hybrid topology covered in the article [Microsoft Hybrid Agent](/exchange/hybrid-deployment/hybrid-agent).

### Migrate from other systems

Other migration options are available for organizations whose source email system is something other than Exchange Server. Other options are also available for organizations that have Personal Storage Table (PST) files they want to migrate to Microsoft 365. These options are outlined in the following sections.

#### Internet Mail Access Protocol (IMAP) migration

If an organization's source email system is an Internet Mail Access Protocol (IMAP) email service, such as Gmail or Yahoo Mail, it can use an IMAP migration to migrate the contents of its user mailboxes to Microsoft 365.

> [!NOTE]
> An IMAP migration isn't limited to migrating email from IMAP-enabled email services. You can also use IMAP migration from Exchange servers. In fact, if your Exchange server is older than Exchange 2003, an IMAP migration is your only option.

You can use the Exchange admin center or Exchange Online PowerShell to run an IMAP migration. To prepare for an IMAP migration, you must:

 -  Add your users into Microsoft 365. Each user must have a target Microsoft 365 mailbox for the IMAP migration.
 -  Create a CSV file of the user mailboxes that you want to migrate, similar to a staged migration.

When you run an IMAP migration, it only copies over email data. It doesn't migrate contacts, calendar items, or tasks. You can migrate a maximum of 500,000 items from a user's mailbox (emails are migrated from newest to oldest). The biggest email you can migrate is 35 MB.

If you limited the connections to your source email system, it's a good idea to increase them to improve migration performance. Common connection limits include:

 -  client/server total connections
 -  per-user connections
 -  IP address connections on either the server or the firewall

To migrate email successfully, Microsoft 365 must connect and communicate with the source email system. Microsoft uses a migration endpoint to accomplish this connection. This endpoint contains the settings that are used to create the connection.

#### PST file migration

You can use the Import service in the Microsoft 365 compliance center to quickly bulk-import PST files to Exchange Online mailboxes in your organization. There are two ways an organization can import PST files to Microsoft 365:

 -  **Network upload**. The organization must upload the PST files over the network to a temporary Azure Storage location in the Microsoft cloud. The organization then runs the Microsoft 365 Import service to import the PST data into its Exchange Online mailboxes.
 -  **Drive shipping**. The organization must copy the PST files to a BitLocker-encrypted hard drive. It must then physically ship the drive to Microsoft. When Microsoft receives the hard drive, data center personnel upload the data to a temporary Azure Storage location in the Microsoft cloud. The organization then runs the Microsoft 365 Import service to import the data into its Exchange Online mailboxes.

An organization should consider a PST migration when:

 -  It has a large amount of mailbox data that needs to be migrated to Microsoft 365.
 -  It runs IMAP/POP3 servers and its clients can export PST files (for example, using Microsoft Outlook).
 -  It doesn't want to overutilize its Internet connectivity during migration.

#### Third-party email migration

An organization should consider a third-party migration when their source email system is any other email server than the ones previously mentioned. A third-party email migration requires a third-party migration tool. There are many tools available from third parties. They use distinctive protocols and approaches to conduct email migrations from email platforms like IBM Lotus Notes and Novell GroupWise.

If the third-party email system only provides POP3 protocol over which users connect to their mailboxes, the only migration option is to use a third-party migration tool or a PST migration.

### Knowledge check

Choose the best response for the following question. Then select “Check your answers.”