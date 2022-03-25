A hybrid Exchange deployment offers organizations the ability to extend to the cloud the feature-rich experience and administrative control they have with their existing on-premises Microsoft Exchange organization. A hybrid deployment provides the look and feel of a single Exchange organization between an on-premises Exchange organization and Exchange Online in Microsoft 365. A hybrid deployment can also serve as an intermediate step to moving completely to an Exchange Online organization.

In a hybrid Exchange deployment, Exchange Online (in the cloud) and the on-premises Exchange Server organization are connected as separate, independent organizations, as shown in the following graphic. Azure AD is the counterpart of a local Active Directory, and Exchange Online is the counterpart for on-premises Exchange Servers.

:::image type="content" source="../media/hybrid-exchange-deployment-a69a15b5.jpg" alt-text="diagram of a hybrid Exchange deployment showing the on-premises Exchange organization and Exchange Online in the cloud are connected with each other as separate, independent organizations":::


An organization must consider the following issues when planning a hybrid Exchange environment:

 -  **Hybrid deployment requirements.** Before an organization configures a hybrid deployment, it must ensure that its on-premises organization meets all the prerequisites required for a successful deployment. For more information, see Hybrid deployment prerequisites.
 -  **Exchange ActiveSync clients.** When an organization moves a mailbox from its on-premises Exchange organization to Exchange Online, all the clients that access the mailbox must be updated to use Exchange Online, including Exchange ActiveSync devices. Most Exchange ActiveSync clients are automatically reconfigured when the mailbox is moved to Exchange Online. However, some older devices may not update correctly. For more information, see [Exchange ActiveSync device settings with Exchange hybrid deployments](/Exchange/activesync-settings?azure-portal=true).
 -  **Mailbox permissions migration.** On-premises mailbox permissions that are explicitly applied on the mailbox are migrated to Exchange Online. These permissions include Send As, Full Access, Send on Behalf of, and folder permissions. Inherited (non-explicit) mailbox permissions and permissions granted to objects that aren’t mail-enabled in Exchange Online aren't migrated. Verify that all permissions are explicitly granted, and all objects are mail enabled before migration. For this reason, an organization must configure these permissions in Microsoft 365 when applicable. For Send As permissions, if the user and the resource attempting to be “sent as” aren’t moved at the same time, the Send As permission must be explicitly added in Exchange Online using the **Add-RecipientPermission** cmdlet.
 -  **Support for cross-premises mailbox permissions.** Exchange hybrid deployments support the use of the Full Access and Send on Behalf Of permissions between mailboxes located in an on-premises Exchange organization and mailboxes located in Microsoft 365. Other steps are required for Send As permissions. Depending on the version of Exchange installed in the on-premises organization, some extra configuration may also be required to support cross-premises mailbox permissions. For more information, see [Configure Exchange to support delegated mailbox permissions in a hybrid deployment](/exchange/hybrid-deployment/set-up-delegated-mailbox-permissions?azure-portal=true).
 -  **Offboarding.** As part of ongoing recipient management, an organization may have to move Exchange Online mailboxes back to its on-premises environment. For more information about how to move mailboxes in hybrid deployments based on Exchange 2013 or newer, see [Move mailboxes between on-premises and Exchange Online organizations in hybrid deployments](/Exchange/hybrid-deployment/move-mailboxes%20?azure-portal=true).
 -  **Mailbox forwarding settings.** Mailboxes can be set up to automatically forward mail sent to them to another mailbox. While mailbox forwarding is supported in Exchange Online, the forwarding configuration isn't copied to Exchange Online when the mailbox is migrated there. Before an organization migrates a mailbox to Exchange Online, it must first export the forwarding configuration for each mailbox. The forwarding configuration is stored in the **DeliverToMailboxAndForward**, **ForwardingAddress**, and **ForwardingSmtpAddress** properties on each mailbox.

Implementing the changes outlined in these considerations will result in the following changes to an Exchange hybrid environment.

:::row:::
  :::column:::
    **Configuration**
  :::column-end:::
  :::column:::
    **Before hybrid deployment**
  :::column-end:::
  :::column:::
    **After hybrid deployment**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Mailbox location
  :::column-end:::
  :::column:::
    Mailboxes on-premises only.
  :::column-end:::
  :::column:::
    Mailboxes on-premises and in Microsoft 365.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Message transport
  :::column-end:::
  :::column:::
    On-premises Mailbox servers handle all inbound and outbound message routing.
  :::column-end:::
  :::column:::
    On-premises Mailbox servers handle internal message routing between the on-premises and Microsoft 365 organization.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Outlook on the web
  :::column-end:::
  :::column:::
    On-premises Mailbox servers receive all Outlook on the web requests and displays mailbox information.
  :::column-end:::
  :::column:::
    On-premises Mailbox servers redirect Outlook on the web requests to either on-premises Exchange 2016 Mailbox servers or provides a link to sign into Microsoft 365.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Unified GAL for both organizations
  :::column-end:::
  :::column:::
    Not applicable; single organization only.
  :::column-end:::
  :::column:::
    On-premises Active Directory synchronization server replicates Active Directory information for mail-enabled objects to Microsoft 365.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Single-sign on used for both organizations
  :::column-end:::
  :::column:::
    Not applicable; single organization only.
  :::column-end:::
  :::column:::
    On-premises Active Directory and Microsoft 365 use the same username and password for mailboxes located either on-premises or in Microsoft 365.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Organization relationship established and a federation trust with Azure AD authentication system
  :::column-end:::
  :::column:::
    Trust relationship with the Azure AD authentication system and organization relationships with other federated Exchange organizations may be configured.
  :::column-end:::
  :::column:::
    Trust relationship with the Azure AD authentication system is required. Organization relationships are established between the on-premises and Microsoft 365.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Free/busy sharing
  :::column-end:::
  :::column:::
    Free/busy sharing between on-premises users only.
  :::column-end:::
  :::column:::
    Free/busy sharing between both on-premises and Microsoft 365 users.
  :::column-end:::
:::row-end:::


**Additional reading.** For more information, see the following article on [Exchange Server Hybrid Deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”