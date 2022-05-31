For most organizations, the volume and complexity of their data is increasing daily—email, documents, instant messages, and more. Effectively managing or governing this information is important because organizations need to:

 -  Comply proactively with industry and government regulations and internal policies that require them to store content for a minimum period of time. For example, some government regulations require organizations to store certain types of content for seven years.
 -  Reduce their risk if there's litigation or a security breach by permanently deleting old content that they're no longer required to keep.
 -  Share knowledge effectively and be more agile by ensuring that their users work only with content that's current and relevant to them.

Retention settings that organizations configure can help them achieve these goals. Managing content commonly requires two actions:

 -  **Retain content.** Prevent permanent deletion and remain available for eDiscovery.
 -  **Delete content.** Permanently delete content from the organization.

With these two retention actions, organizations can configure retention settings for the following outcomes:

 -  **Retain-only.** Keep content forever or for a specified period of time.
 -  **Delete-only.** Permanently delete content after a specified period of time.
 -  **Retain and then delete.** Keep content for a specified period of time and then permanently delete it.

These retention settings that work with content in place saves organizations the extra overhead of creating and configuring extra storage when they need to retain content for compliance reasons. They also save organizations from having to implement customized processes to copy and synchronize this data.

### How retention settings work with content in place

Organizations use retention policies to implement retention settings. Retention policies enable organizations to proactively decide whether to retain content, delete content, or retain and then delete the content. A retention policy enables organizations to efficiently manage their data. It does so by assigning the same retention settings at the container level to be automatically inherited by content in that container.

When content has retention settings assigned to it, users can continue to edit and work with the content as if nothing’s changed. They're able to do so because the content is retained in place, in its original location. But if they edit or delete content that’s included in the retention policy, a copy of the content as it existed when the policy was applied is saved to a secure location. The copy is kept in this location in its original state while the policy is in effect.

 -  For SharePoint and OneDrive sites, a copy of the original content is kept in the **Preservation Hold** library when users edit or delete it.

    > [!NOTE]
    > The Preservation Hold library is included in the site's storage quota. As such, an organization may need to increase its storage when it uses retention settings for SharePoint and Microsoft 365 groups.

 -  For Exchange mailboxes, the copy is retained in the **Recoverable Items** folder.
 -  For Teams and Yammer messages, the copy is retained in a hidden folder named **SubstrateHolds**. This folder is a subfolder in the Exchange **Recoverable Items** folder.

These secure locations and the retained content aren't visible to most people. In most cases, people don't even need to know that their content is subject to retention settings.

**Additional reading**. For detailed information about how retention settings work for different workloads, see the following articles:

 -  [Learn about retention for SharePoint and OneDrive](/microsoft-365/compliance/retention-policies-sharepoint?azure-portal=true).
 -  [Learn about retention for Microsoft Teams](/microsoft-365/compliance/retention-policies-teams?azure-portal=true).
 -  Learn about retention for Yammer.
 -  [Learn about retention for Exchange](/microsoft-365/compliance/retention-policies-exchange?azure-portal=true).

### Retention policies and retention labels

An organization can assign its retention settings to content by using retention policies and retention labels with label policies. Just one of these methods can be used, or they can be combined together.

A retention policy can assign the same retention settings for content at a site or mailbox level. It can also use a retention label to assign retention settings at an item level, such as a folder, document, or email.

For example, let's assume that Contoso wants to retain all documents in a SharePoint site for five years. It's more efficient to implement this plan with a retention policy than to apply the same retention label to all documents in that site. However, if some documents in that site must be retained for five years and others retained for 10 years, a retention policy wouldn't be able to accommodate this situation. When you need to specify retention settings at the item level, retention labels must be used.

Unlike retention policies, retention settings from retention labels travel with the content if it's moved to a different location within a company's Microsoft 365 tenant. In addition, retention labels have the following capabilities that retention policies don't support:

 -  Options to start the retention period from when the content was:
     -  labeled
     -  based on an event
     -  created (the age of the content)
     -  last modified
 -  Use [trainable classifiers](/microsoft-365/compliance/classifier-learn-about?azure-portal=true) to identify content to label.
 -  Apply a default label for SharePoint items or Exchange messages.
 -  [Supported actions at the end retention period:](/microsoft-365/compliance/disposition?azure-portal=true)
     -  [Disposition review](/microsoft-365/compliance/disposition?azure-portal=true) to review the content before it's permanently deleted.
     -  Automatically apply another retention label.
 -  Mark the content as a [record](/microsoft-365/compliance/records-management?azure-portal=true) as part of the label settings.
 -  Have [proof of disposition](/microsoft-365/compliance/disposition?azure-portal=true) when content is deleted at the end of its retention period.

#### Retention policies

Retention policies can be applied to the following locations:

 -  Exchange email
 -  SharePoint site
 -  OneDrive accounts
 -  Microsoft 365 Groups
 -  Skype for Business
 -  Exchange public folders
 -  Teams channel messages
 -  Teams chats
 -  Teams private channel messages
 -  Yammer community messages
 -  Yammer user messages

Organizations can efficiently apply a single policy to multiple locations, or to specific locations or users.

For the start of the retention period, an organization can choose when the content was created or last modified. The last modified date is only supported for files and the SharePoint, OneDrive, and Microsoft 365 Groups locations.

Items inherit the retention settings from their container that's specified in the retention policy. If the items are later moved outside that container when the policy is configured to retain content, a copy of that item is retained in the workload's secured location. However, the retention settings don't travel with the content in its new location. If that's required, use retention labels instead of retention policies.

#### Retention labels

Retention labels should be used for different types of content that require different retention settings. For example:

 -  Tax forms that must be retained for a minimum period of time.
 -  Press materials that must be permanently deleted when they reach a specific age.
 -  Competitive research that must be retained for a specific period and then permanently deleted.
 -  Work visas that must be marked as a record so they can't be edited or deleted.

> [!IMPORTANT]
> In all these cases, retention labels let you apply retention settings for governance control at the item level (document or email).

With retention labels, organizations can:

 -  Enable their users to apply a retention label manually to content in Outlook and Outlook on the web, OneDrive, SharePoint, and Microsoft 365 groups. Users often know best what type of content they're working with. As such, they can classify it and have the appropriate retention settings applied.
 -  Apply retention labels to content automatically if it matches specific conditions. These conditions include cloud attachments that are shared in email or Teams, or when the content contains:
     -  Specific types of sensitive information.
     -  Specific keywords that match a query you create.
     -  Pattern matches for a trainable classifier.
 -  Start the retention period from when the content was labeled for documents in SharePoint sites and OneDrive accounts, and for email items.
 -  Start the retention period when an event occurs. For example, when an employee leaves the organization, or a contract expires.
 -  Apply a default retention label to a document library, folder, or document set in SharePoint. The label should be designed so that all documents that are stored in that location inherit the default retention label.
 -  Mark items as a record as part of their [records management](/microsoft-365/compliance/records-management?azure-portal=true) strategy. When this labeled content remains in Microsoft 365, further restrictions are placed on the content that may be needed for regulatory reasons. For more information, see Compare restrictions for what actions are allowed or blocked.

Unlike [sensitivity labels](/microsoft-365/compliance/sensitivity-labels?azure-portal=true), retention labels don't persist if the content is moved outside Microsoft 365.

### Classifying content without applying any actions

Although the main purpose of retention labels is to retain or delete content, you can also use retention labels without turning on any retention or other actions. In this case, you can use a retention label simply as a text label, without enforcing any actions.

For example, you can create and apply a retention label named "Review later" with no actions. You can then use that label to find that content later.

:::image type="content" source="../media/retention-label-retention-off-option-8bfecb9d.png" alt-text="Screenshot of the retention label option titled Just label items, which only classifies labeled items but doesn't retain them.":::


### Using a retention label as a condition in a DLP policy

You can specify a retention label as a condition in a Microsoft Purview Data Loss Prevention (DLP) policy for documents in SharePoint. For example, you can configure a DLP policy to prevent documents from being shared outside the organization if they have a specified retention label applied to it.

**Additional reading**. For more information, see [Using a retention label as a condition in a DLP policy](/microsoft-365/compliance/data-loss-prevention-policies?azure-portal=true).

### Retention labels and policies that apply them

When you publish retention labels, they're included in a retention label policy. By doing so, the labels become available for admins and users to apply to content. The following diagram shows the two options in this design:

1.  A single retention label can be included in multiple retention label policies.
2.  Retention label policies specify the locations to publish the retention labels. The same location can be included in multiple retention label policies.

:::image type="content" source="../media/retention-labels-and-policies-45aabfc1.png" alt-text="Diagram showing how retention labels can be added to label policies that specify locations.":::


You can also create one or more auto-apply retention label policies, each with a single retention label. With this policy, a retention label is automatically applied when conditions that you specify in the policy are met.

### Retention label policies and locations

Retention labels can be published to different locations, depending on what the retention label does.

:::row:::
  :::column:::
    **If the retention label is...**
  :::column-end:::
  :::column:::
    **Then the label policy can be applied to...**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Published to admins and end users.
  :::column-end:::
  :::column:::
    Exchange, SharePoint, OneDrive, Microsoft 365 Groups
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Auto-applied based on sensitive information types or trainable classifiers.
  :::column-end:::
  :::column:::
    Exchange, SharePoint, OneDrive
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Auto-applied based on keywords or a query.
  :::column-end:::
  :::column:::
    Exchange, SharePoint, OneDrive, Microsoft 365 Groups
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Auto-applied to cloud attachments.
  :::column-end:::
  :::column:::
    SharePoint, OneDrive, Microsoft 365 Groups
  :::column-end:::
:::row-end:::


Exchange public folders, Skype, Teams, and Yammer messages don't support retention labels. To retain and delete content from these locations, retention policies must be used.

### Only one retention label at a time

An email or document can only have a single retention label applied to it at a time. A retention label can be applied [manually](/microsoft-365/compliance/create-apply-retention-labels?azure-portal=true) by an end user or admin. It can also be applied automatically by using any of the following methods:

 -  [Auto-apply label policy](/microsoft-365/compliance/apply-retention-labels-automatically?azure-portal=true)
 -  [Document understanding model for SharePoint Syntex](/microsoft-365/contentunderstanding/apply-a-retention-label-to-a-model?azure-portal=true)
 -  [Default label for SharePoint](/microsoft-365/compliance/create-apply-retention-labels?azure-portal=true#applying-a-default-retention-label-to-all-content-in-a-sharepoint-library-folder-or-document-set) or [Outlook](/microsoft-365/compliance/create-apply-retention-labels?azure-portal=true#applying-a-default-retention-label-to-an-outlook-folder)
 -  [Outlook rules](/microsoft-365/compliance/create-apply-retention-labels?azure-portal=true#automatically-applying-a-retention-label-to-email-by-using-rules)

For standard retention labels (they don't mark items as a [record or regulatory record](/microsoft-365/compliance/records-management?azure-portal=true)):

 -  Admins and end users can manually change or remove an existing retention label that's applied on content.
 -  When content already has a retention label applied, the existing label won't be automatically removed or replaced by another retention label.

    > [!NOTE]
    > There's one exception to this rule, which is when the existing label was applied as a default label. When you use a default label, there are some scenarios when it can be replaced by another default label, or automatically removed.

 -  When content already has a retention label applied, the existing label won't be automatically removed or replaced by another retention label with two possible exceptions:
     -  The existing label is configured to automatically apply a different retention label at the end of the retention period.
     -  The existing label was applied as a default label. When you use a default label, there are some scenarios when it can be replaced by another default label, or automatically removed.For more information about the label behavior when it's applied by using a default label:
     -  **Default label for SharePoint**. [Label behavior when you use a default label for SharePoint](/microsoft-365/compliance/create-apply-retention-labels?azure-portal=true#label-behavior-when-you-use-a-default-label-for-sharepoint).
     -  **Default label for Outlook**. [Applying a default retention label to an Outlook folder](/microsoft-365/compliance/create-apply-retention-labels?azure-portal=true#applying-a-default-retention-label-to-an-outlook-folder).
 -  If there are multiple auto-apply label policies that could apply a retention label, and content meets the conditions of multiple policies, the retention label for the oldest auto-apply label policy (by date created) is applied.

When retention labels mark items as a record or a regulatory record, these labels are never automatically changed during their configured retention period. Only admins for the container can manually change or remove retention labels that mark items as a record, but not regulatory records. For more information, see [Compare restrictions for what actions are allowed or blocked](/microsoft-365/compliance/records-management?azure-portal=true#compare-restrictions-for-what-actions-are-allowed-or-blocked).

### Policy lookup

An organization can configure multiple retention policies for Microsoft 365 locations. It can also configure multiple retention label policies that it publishes or automatically applies. To find the policies for retention that are assigned to specific users, sites, and Microsoft 365 groups, select the **Policy lookup** tab in either the **Data lifecycle management** or **Records management solutions** in the **Microsoft Purview compliance** portal.

For example:

:::image type="content" source="../media/policy-lookup-01e82ffb.png" alt-text="Screenshot showing the Policy lookup tab on the Data lifecycle management screen.":::


You must specify one of the following options:

 -  The exact email address for a user.
 -  The exact URL for a site.
 -  The exact email address for a Microsoft 365 group.

You can't use wildcards, or partial matches.

The exact URL option for sites includes OneDrive accounts. For information how to specify the URL for a user's OneDrive account, see [Get a list of all user OneDrive URLs in your organization](/onedrive/list-onedrive-urls).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”