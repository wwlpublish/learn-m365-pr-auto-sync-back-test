A hybrid Exchange deployment offers organizations the ability to extend to the cloud the feature-rich experience and administrative control they have with their existing on-premises Microsoft Exchange organization. A hybrid deployment provides the look and feel of a single Exchange organization between an on-premises Exchange organization and Exchange Online in Microsoft 365. In addition, a hybrid deployment can serve as an intermediate step to moving completely to an Exchange Online organization.

It's important to note that in a hybrid Exchange deployment, the on-premises Exchange organization and Exchange Online in the cloud are connected as separate, independent organizations, as shown in the following graphic. Azure AD is the counterpart of a local Active Directory, and Exchange Online is the counterpart for on-premises Exchange servers.

:::image type="content" source="../media/hybrid-exchange-deployment-a69a15b5.jpg" alt-text="diagram of a hybrid Exchange deployment showing the on-premises Exchange organization and Exchange Online in the cloud are connected with each other as separate, independent organizations":::


When planning your hybrid Exchange environment, you must consider the following issues:

 *  **Hybrid deployment requirements.** Before you configure a hybrid deployment, you need to make sure your on-premises organization meets all the prerequisites required for a successful deployment. For more information, see [Hybrid deployment prerequisites](https://docs.microsoft.com/Exchange/hybrid-deployment-prerequisites%20?azure-portal=true).
 *  **Exchange ActiveSync clients.** When you move a mailbox from your on-premises Exchange organization to Exchange Online, all the clients that access the mailbox must be updated to use Exchange Online, including Exchange ActiveSync devices. Most Exchange ActiveSync clients are automatically reconfigured when the mailbox is moved to Exchange Online; however, some older devices might not update correctly. For more information, see [Exchange ActiveSync device settings with Exchange hybrid deployments:::image type="content" source="":::
    ](https://docs.microsoft.com/Exchange/activesync-settings?azure-portal=true).
 *  **Mailbox permissions migration.** On-premises mailbox permissions that are explicitly applied on the mailbox are migrated to Exchange Online. These permissions include, and are not limited to, Send As, Full Access, Send on Behalf of, and folder permissions. Inherited (non-explicit) mailbox permissions and permissions granted to objects that aren’t mail-enabled in Exchange Online are not migrated. Verify that all permissions are explicitly granted and all objects are mail enabled prior to migration. Therefore, you must plan for configuring these permissions in Microsoft 365 if applicable for your organization. For Send As permissions, if the user and the resource attempting to be “sent as” aren’t moved at the same time, you'll need to explicitly add the Send As permission in Exchange Online using the Add-RecipientPermission cmdlet.
 *  **Support for cross-premises mailbox permissions.** Exchange hybrid deployments support the use of the Full Access and Send on Behalf Of permissions between mailboxes located in an on-premises Exchange organization and mailboxes located in Microsoft 365. Additional steps are required for Send As permissions. Also, some extra configuration may be required to support cross-premises mailbox permissions depending on the version of Exchange installed in your on-premises organization. For more information, see [Configure Exchange to support delegated mailbox permissions in a hybrid deployment](https://docs.microsoft.com/exchange/hybrid-deployment/set-up-delegated-mailbox-permissions?azure-portal=true).
 *  **Offboarding.** As part of ongoing recipient management, you might have to move Exchange Online mailboxes back to your on-premises environment. For more information about how to move mailboxes in hybrid deployments based on Exchange 2013 or newer, see [Move mailboxes between on-premises and Exchange Online organizations in hybrid deployments](https://docs.microsoft.com/Exchange/hybrid-deployment/move-mailboxes%20?azure-portal=true).
 *  **Mailbox forwarding settings.** Mailboxes can be set up to automatically forward mail sent to them to another mailbox. While mailbox forwarding is supported in Exchange Online, the forwarding configuration isn't copied to Exchange Online when the mailbox is migrated there. Before you migrate a mailbox to Exchange Online, make sure you export the forwarding configuration for each mailbox. The forwarding configuration is stored in the DeliverToMailboxAndForward, ForwardingAddress, and ForwardingSmtpAddress properties on each mailbox.

Implementing the changes outlined in these considerations will result in the following changes to an Exchange hybrid environment.

:::row:::
  :::column:::
    <p><b>Configuration </b></p>
  :::column-end:::
  :::column:::
    <p><b>Before hybrid deployment </b></p>
  :::column-end:::
  :::column:::
    <p><b>After hybrid deployment </b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Mailbox location</p>
  :::column-end:::
  :::column:::
    <p>Mailboxes on-premises only.</p>
  :::column-end:::
  :::column:::
    <p>Mailboxes on-premises and in Microsoft 365.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Message transport</p>
  :::column-end:::
  :::column:::
    <p>On-premises Mailbox servers handle all inbound and outbound message routing.</p>
  :::column-end:::
  :::column:::
    <p>On-premises Mailbox servers handle internal message routing between the on-premises and Microsoft 365 organization.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Outlook on the web</p>
  :::column-end:::
  :::column:::
    <p>On-premises Mailbox servers receive all Outlook on the web requests and displays mailbox information.</p>
  :::column-end:::
  :::column:::
    <p>On-premises Mailbox servers redirect Outlook on the web requests to either on-premises Exchange 2016 Mailbox servers or provides a link to sign into Microsoft 365.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Unified GAL for both organizations</p>
  :::column-end:::
  :::column:::
    <p>Not applicable; single organization only.</p>
  :::column-end:::
  :::column:::
    <p>On-premises Active Directory synchronization server replicates Active Directory information for mail-enabled objects to Microsoft 365.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Single-sign on used for both organizations</p>
  :::column-end:::
  :::column:::
    <p>Not applicable; single organization only.</p>
  :::column-end:::
  :::column:::
    <p>On-premises Active Directory and Microsoft 365 use the same username and password for mailboxes located either on-premises or in Microsoft 365.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Organization relationship established and a federation trust with Azure AD authentication system</p>
  :::column-end:::
  :::column:::
    <p>Trust relationship with the Azure AD authentication system and organization relationships with other federated Exchange organizations may be configured.</p>
  :::column-end:::
  :::column:::
    <p>Trust relationship with the Azure AD authentication system is required. Organization relationships are established between the on-premises and Microsoft 365.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Free/busy sharing</p>
  :::column-end:::
  :::column:::
    <p>Free/busy sharing between on-premises users only.</p>
  :::column-end:::
  :::column:::
    <p>Free/busy sharing between both on-premises and Microsoft 365 users.</p>
  :::column-end:::
:::row-end:::


**Additional reading.** For more information, see the following article on [Exchange Server Hybrid Deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx?azure-portal=true).