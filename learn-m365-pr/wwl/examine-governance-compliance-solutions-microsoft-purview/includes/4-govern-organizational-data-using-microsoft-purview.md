Microsoft Purview Data Lifecycle Management provides organizations with tools and capabilities to retain the content they need to keep, and delete the content they don't. Retaining and deleting content is often needed for compliance and regulatory requirements. However, deleting content that no longer has business value also helps organizations manage risk and liability. For example, it reduces an organization's attack surface.

Retention policies are the cornerstone for data lifecycle management. These policies should be used for Microsoft 365 workloads that include Exchange, SharePoint, OneDrive, Teams, and Yammer. An organization should configure whether content for these services must be retained indefinitely, or for a specific period if users edit or delete it. Or it can configure the policy to permanently delete the content automatically after a specified period if it's not already deleted. These two actions can also be combined for retention and then deletion. This scenario is a typical configuration. For example, retain email for three years and then delete it.

When you configure a retention policy, you can target one of the following instances:

 -  All instances in your organization, such as all mailboxes and all SharePoint sites.
 -  Individual instances, such as only the mailboxes for specific departments or regions, or selected SharePoint sites.

Organizations sometimes need exceptions for individual emails or documents. For example, they may require a longer retention period for legal documents. Organizations can create these exceptions be using retention labels they publish to apps. By doing so, users can apply them, or automatically apply them by inspecting the content.

**Additional reading**. For more information about retention policies and retention labels, and how retention works in Microsoft 365, see [Learn about retention policies and retention labels](/microsoft-365/compliance/retention?azure-portal=true).

> [!NOTE]
> Some organizations must manage high-value items for business, legal, or regulatory record-keeping requirements. In these scenarios, use retention labels with [records management](/microsoft-365/compliance/records-management?azure-portal=true) rather than retention labels with data lifecycle management.

Other data lifecycle management capabilities to help organizations keep what they need and delete what they don't include:

 -  **Mailbox archiving**. Provides users with extra mailbox storage space. Also provides auto-expanding archiving for mailboxes that need more than 100 GB of storage. A default archiving policy automatically moves email to the archive mailbox. If necessary, you can customize this policy. For more information about mailbox archiving, see [Learn about archive mailboxes](/microsoft-365/compliance/archive-mailboxes?azure-portal=true).
 -  **Inactive mailboxes**. They retain mailbox content after employees leave the organization. For more information about inactive mailboxes, see [Learn about inactive mailboxes](/microsoft-365/compliance/inactive-mailboxes-in-office-365?azure-portal=true).
 -  **Import service for PST files**. To do so, use network upload or drive shipping. For more information, see [Learn about importing your organization's PST files](/microsoft-365/compliance/importing-pst-files-to-office-365?azure-portal=true).

### Get started with Microsoft Purview Data Lifecycle Management

When an organization is ready to start governing its data by retaining the content that it must keep and deleting the content that it doesn't, it should use the following guidance for Microsoft Purview Data Lifecycle Management:

1.  **Understand how retention and deletion works in Microsoft 365**. Based on this knowledge, the organization can then identify the workloads that need a retention policy and whether it must create retention labels for exceptions. For more information, see [Learn about retention](/microsoft-365/compliance/retention?azure-portal=true).
    
    > [!NOTE]
    > Organizations that manage high-value items for business, legal, or regulatory record-keeping requirements should use retention labels with [records management](/microsoft-365/compliance/records-management?azure-portal=true) rather than data lifecycle management.
2.  **Create retention policies for the workloads you identified**. Specify retention settings and actions that are required by your organization policies or industry regulations. For more information, see [Create retention policies](/microsoft-365/compliance/create-retention-policies?azure-portal=true).
    
    If needed, [create and apply retention labels for your exceptions](/microsoft-365/compliance/create-retention-labels-information-governance?azure-portal=true).
3.  **Enable mailbox archiving**. Archiving provides users with extra mailbox storage space. For more information, see [Enable archive mailboxes in the Microsoft Purview compliance portal](/microsoft-365/compliance/enable-archive-mailboxes?azure-portal=true).
    
    When organizations must support archive mailboxes, they should:
    
    
     -  [Enable auto-expanding archiving](/microsoft-365/compliance/enable-autoexpanding-archiving?azure-portal=true) for mailboxes that need more than 100-GB of storage.
     -  Use [retention tags with a retention policy from messaging records management (MRM)](/microsoft-365/compliance/set-up-an-archive-and-deletion-policy-for-mailboxes?azure-portal=true) if you either need to:
         -  Customize how emails are automatically moved from a user's primary mailbox to their archive mailbox.
         -  Specify retention and deletion settings for specific folders rather than the whole mailbox.
4.  **Understand and manage inactive mailboxes**. Focus on inactive mailboxes that retain mailbox content after employees leave the organization. For more information, see [Learn about inactive mailboxes](/microsoft-365/compliance/inactive-mailboxes-in-office-365?azure-portal=true).
5.  **Import PST files**. If you have PST files that contain data you want to govern, import the files to online mailboxes by using network upload or drive shipping. For more information, see [Learn about importing your organization's PST files](/microsoft-365/compliance/importing-pst-files-to-office-365?azure-portal=true).

### Subscription and licensing requirements

Many different subscriptions support data lifecycle management capabilities. To see the options for licensing your users to benefit from Microsoft Purview features, see the [Microsoft 365 licensing guidance for security &amp; compliance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guid?azure-portal=trueance).

### Permissions

For permissions to manage mailboxes for archiving, inactive mailboxes, and import, these typically require Exchange permissions, such as the Mail Recipients role. By default, this role is assigned to the Recipient Management and Organization Management role groups.

#### Permissions for retention policies and retention labels

Members of your compliance team who will create and manage retention policies and retention labels need permissions to the Microsoft Purview compliance portal. By default, the tenant admin (global administrator) has access to this location and can give compliance officers and other people access without giving them all the permissions of a tenant admin. To grant permissions for this limited administration, it's recommended that you add users to the Compliance Administrator admin role group.

Alternatively to using this default role, you can create a new role group and add the Retention Management role to this group. For a read-only role, use View-Only Retention Management.

For instructions to add users to the default roles or create your own role groups, see [Permissions in the Microsoft Purview compliance portal](/microsoft-365/compliance/microsoft-365-compliance-center-permissions?azure-portal=true).

These permissions are required only to create, configure, and apply retention policies and retention labels. The person configuring these policies and labels doesn't require access to the content.

### Common scenarios

Use the following table to help you map your business requirements to the most common scenarios for data lifecycle management.

:::row:::
  :::column:::
    **I want to ...**
  :::column-end:::
  :::column:::
    **Documentation**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Efficiently retain or delete data for Microsoft 365 services:
\- Exchange
\- SharePoint
\- OneDrive
\- Microsoft 365 Groups
\- Teams
\- Yammer
\- Skype for Business
  :::column-end:::
  :::column:::
    [Create and configure retention policies](/microsoft-365/compliance/create-retention-policies?azure-portal=true)
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Provide users with extra mailbox storage.
  :::column-end:::
  :::column:::
    [Enable archive mailboxes in the Microsoft Purview compliance portal](/microsoft-365/compliance/enable-archive-mailboxes?azure-portal=true)
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Retain mailbox data after employees leave the organization.
  :::column-end:::
  :::column:::
    [Create and manage inactive mailboxes](/microsoft-365/compliance/create-and-manage-inactive-mailboxes?azure-portal=true)
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Upload mailbox data from PST files.
  :::column-end:::
  :::column:::
    [Use network upload to import PST files](/microsoft-365/compliance/use-network-upload-to-import-pst-files?azure-portal=true)
  :::column-end:::
:::row-end:::


If you have a scenario that requires data management of individual items, see the [common scenarios for records management](/microsoft-365/compliance/get-started-with-records-management?azure-portal=true#common-scenarios?azure-portal=true).

### End-user documentation

The Microsoft Purview Data Lifecycle Management capabilities that support mailbox management (archiving, inactive mailboxes, and import) typically don't require end-user documentation.

#### End-user documentation for retention and deletion

Most retention policies work unobtrusively in the background without user interaction. As such, little documentation is needed for end users. Retention policies for Teams inform users when their messages have been deleted with a link to [Teams messages about retention policies](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b?azure-portal=true).

However, if you supplement retention policies with retention labels, these labels do have a UI presence in Microsoft 365 apps. Before you deploy these labels to your production network, ensure you provide information and instructions for end users and your help desk. To help users apply retention labels in SharePoint and OneDrive, see [Apply retention labels to files in SharePoint or OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df?azure-portal=true).

The most effective end-user documentation will always be customized guidance and instructions you provide for the retention label names and configurations you choose.

**Additional reading**. For more information, see the following article for downloads that you can use to help train your users: [End User Training for Retention Labels](https://microsoft.github.io/ComplianceCxE/enduser/retention/?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”