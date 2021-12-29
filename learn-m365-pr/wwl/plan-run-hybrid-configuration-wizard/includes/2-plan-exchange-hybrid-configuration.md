An Exchange hybrid configuration is a connection from either a single or multiple on-premises Exchange organization(s) to a single Exchange Online organization in a Microsoft 365 tenant. The term "hybrid" represents the cross-premises connectivity between local and cloud Exchange organizations.

Exchange hybrid is commonly used for mid-term to long-term coexistence, where mailboxes must are stored in both on-premises and Exchange Online for compliance and security purposes. Exchange hybrid provides a smooth migration path to Microsoft 365 because you don’t need to consider changing Outlook profiles when moving your users to the cloud. Instead, the Outlook profiles are automatically changed for you.

A hybrid configuration offers a complete email experience, with the ability to extend your on-premises Exchange organization to Exchange Online. It provides a seamless look and feel, as if the users belong to a single Exchange organization.

### The Hybrid Configuration Wizard

The Hybrid Configuration Wizard (HCW) is the tool used for setting up a hybrid configuration between your on-premises Exchange organization and Microsoft 365. The HCW is an application that runs directly from a computer or server in your organization. You can use the HCW to configure the following two hybrid configuration options:

 -  Full hybrid configuration
 -  Minimal hybrid configuration

The following screenshot displays the HCW page that's used for selecting the hybrid configuration option you plan to deploy.

:::image type="content" source="../media/hybrid-configuration-wizard-beda00f2.png" alt-text="screenshot displaying the HCW page that is used for selecting the hybrid configuration option you plan to deploy":::


### Minimal hybrid configuration

Microsoft introduced the minimal hybrid configuration for the following reasons:

 -  The cutover and staged migration experiences are labor-intensive on the client side.
 -  To provide a better user migration experience when a full hybrid configuration isn't needed.

A minimal hybrid configuration provides a quick way to move to Exchange Online, and a reasonable option for both the administrator and users. As such, minimal hybrid configuration enables organizations to only complete migrations and administration in a hybrid deployment. It doesn't include complex configurations such as Exchange Federation or secure email flow.

The main benefit to a minimal hybrid configuration is that it enables organizations to have the same user migration experience as in a full hybrid configuration:

 -  User account credentials are synchronized to Azure AD and Exchange Online using Azure AD Connect.
 -  The mailbox move will be online; the client doesn't need to disconnect from their mail client during the mailbox move.
 -  The Outlook profile is automatically updated once the mailbox move is finished. As such, it doesn't require any administrative intervention.
 -  No other connectors will be created. The existing mail flow between your Exchange on-premises environment and Exchange Online is used.

The technical requirements for a minimal hybrid configuration are similar to a full hybrid configuration:

 -  Azure AD Connect for directory synchronization of your local Active Directory environment is required.
 -  All SMTP domains that you plan to use in Exchange Online must be registered and verified with the Microsoft 365 tenant.
 -  Unless you can use the Modern Hybrid (described later), you must configure your Mailbox Replication Services (MRS) Migration Endpoint using a trusted third-party TLS/SSL certificate. This certificate is typically the URL you use to publish Exchange Web Service externally.
 -  You don't need any DNS TXT records for a Federated domain proof since no federation is configured in a minimal hybrid configuration.
 -  Your SMTP connectors don't need a certificate, nor do they need to be configured to allow TLS.

### Full hybrid configuration

A full hybrid configuration includes configuring the full feature set to configure the best Exchange hybrid experience for your users. A full hybrid configuration is typically used when an organization faces one of the following scenarios:

 -  It plans a longer coexistence between Exchange and Exchange Online.
 -  Its Exchange organization is so large that it can't be migrated over a short period of time, such as a weekend.

A full hybrid configuration includes two hybrid connectivity options: Exchange Classic Hybrid and Exchange Modern Hybrid. The following table identifies the difference between the two approaches.

:::row:::
  :::column:::
    **Hybrid Connectivity**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
  :::column:::
    **When to use**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Exchange Classic Hybrid
  :::column-end:::
  :::column:::
    This option is the traditional hybrid approach in the following scenarios:

 -  Exchange Online can connect to your Exchange Servers over the Internet.
 -  Your Exchange Servers can connect to Exchange Online over the Internet.

This option requires that your Exchange Servers be accessible over the Internet. You must also own an officially trusted third-party certificate.
  :::column-end:::
  :::column:::
    Ideal if you already published your Exchange endpoints, such as Outlook on the web, to the Internet.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Exchange Modern Hybrid
  :::column-end:::
  :::column:::
    This option installs the Hybrid Agent that takes over the communication between Exchange Online and your on-premises Exchange Servers.
  :::column-end:::
  :::column:::
    You should consider this option when you didn't publish Exchange to the Internet, or you didn't purchase official third-party certificates.
  :::column-end:::
:::row-end:::


A full hybrid configuration offers all functionality of a minimal hybrid configuration, plus the following features:

 -  Exchange Online and on-premises users can share free/busy calendar data.
 -  Administrators can use their familiar Exchange management tools, namely the Exchange admin center and Exchange Management Shell (or Windows PowerShell), to manage and move users to Exchange Online.
 -  When migrating mailboxes, Outlook profiles for users are automatically updated to the Exchange Online environment when the Exchange hybrid deployment and Autodiscover is configured properly. Administrators don't need to manually reconfigure Outlook profiles or resynchronize .OST files after moving users’ mailboxes.
 -  Outlook on the web redirection allows users to use the well-known Outlook on the web URL to access their mailbox on the web. You must specify a target URL for your organization (for example, https://outlook.com/owa/contoso.com).
 -  MailTips, internal out-of-office messages, and similar features are available to both cloud and on-premises mailboxes so the user can't see a difference.
 -  Delivery reports and multi-mailbox search work with users who are on-premises and those users who work in Exchange Online.
 -  Authentication headers are preserved during cross-premises mail flow, so all mail looks and feels like it's internal to the company (for example, recipient names resolve in the global address list).
 -  If necessary, administrators can easily move mailboxes back to the on-premises Exchange environment.
 -  Support for archive mailboxes located in Exchange Online for on-premises users.
 -  Support for Public Folder coexistence with Legacy and Modern Public Folders located on Exchange on-premises.
 -  Cross-premises OAuth support since Exchange Server 2013 SP1.
 -  Cross-premises eDiscovery Search with SharePoint Online since Exchange Server 2013 SP1.
 -  Modern Attachments stored in OneDrive for Business Online since Exchange Server 2016
 -  Microsoft Teams integration for on-premises Mailboxes, including meeting and calendar integration when using OAuth and Exchange Server 2016 CU3 and higher.
 -  Support for Hybrid Modern Authentication with Exchange 2013 CU19 and higher, Exchange 2016 CU8 and higher and Exchange 2019, allowing Azure AD identities secured by Microsoft 365 technologies to be used for on-premises sign-in and use of the Outlook App.
 -  Limited support from Microsoft 365 groups for on-premises mailboxes.
 -  Other limitations include:
    
     -  On-premises users can't use links included in group message footers.
     -  On-premises users can't become an administrator of a Microsoft 365 group.

> [!NOTE]
> As mentioned earlier, a full hybrid configuration can serve as an intermediate step to moving completely to an Exchange Online organization. It can also be used to remain in long-term coexistence with your existing Exchange on-premises environment.

### Considerations when choosing minimal or full hybrid configuration

You should consider the following issues when determining whether to use a minimal or full hybrid configuration.

:::row:::
  :::column:::
    **Hybrid configuration option**
  :::column-end:::
  :::column:::
    **When to use**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Minimal Hybrid Configuration
  :::column-end:::
  :::column:::
    This option is intended for small or medium-sized organizations that need a seamless migration experience for their users. Typically, this option is used in scenarios where hybrid is used as a migration option that doesn't require enhanced features.
One of the significant advantages in using this migration option is that your users can keep their Outlook OST files and they don’t need to resynchronize. You can also move mailboxes back to your on-premises Exchange. The minimal hybrid configuration is also an excellent solution for a quick onboarding during merger and acquisition scenarios.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Full Hybrid Configuration
  :::column-end:::
  :::column:::
    This option should be used if you plan a long-term coexistence between Exchange on-premises and Exchange Online that requires the most features available for your users. Organizations who require advanced coexistence functionality such as sharing of free / busy and calendar data between on-premises and Exchange Online, typically tend to implement a full hybrid configuration.
In this scenario, users can collaborate as they’re in the same organization. Another important point is that in a hybrid configuration, an organization can move its mailboxes between its on-premises Exchange and Exchange Online in any direction.
  :::column-end:::
:::row-end:::


## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.