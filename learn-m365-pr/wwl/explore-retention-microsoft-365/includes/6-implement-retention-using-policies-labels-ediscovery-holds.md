Retention settings and [holds that you create with an eDiscovery case](/microsoft-365/compliance/create-ediscovery-holds?azure-portal=true) can both prevent data from being permanently deleted. However, these two forms of retention are designed for different scenarios. To help you understand the differences and decide which to use, use the following guidance:

 -  **Retention settings**. The settings that you specify in retention policies and retention labels are designed for a long-term data lifecycle management strategy. The purpose of these settings is to retain or delete data for compliance requirements. Usually, the scope is broad, with the main focus being the location and content rather than individual users. The start and end of the retention period is configurable. Content can also be automatically deleted without administrator intervention.
 -  **Holds for eDiscovery**. eDiscovery holds can be created for eDiscovery (Standard) and eDiscovery (Premium) cases. In both instances, they're designed for a limited duration to preserve data for a legal investigation. The scope is specific with the focus being content owned by identified users. The start and end of the preservation period isn't configurable. Instead, it's dependent on individual administrator actions, without an option to automatically delete content when the hold is released.

The following table provides a summarized comparison of retention settings versus eDiscovery holds.

:::row:::
  :::column:::
    **Consideration**
  :::column-end:::
  :::column:::
    **Retention**
  :::column-end:::
  :::column:::
    **eDiscovery holds**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Business need:
  :::column-end:::
  :::column:::
    Compliance
  :::column-end:::
  :::column:::
    Legal
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Time scope:
  :::column-end:::
  :::column:::
    Long-term
  :::column-end:::
  :::column:::
    Short-term
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Focus:
  :::column-end:::
  :::column:::
    Broad, content-based
  :::column-end:::
  :::column:::
    Specific, user-based
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Start and end date configurable:
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    No
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Content deletion:
  :::column-end:::
  :::column:::
    Yes (optional)
  :::column-end:::
  :::column:::
    No
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Administrative overheads:
  :::column-end:::
  :::column:::
    Low
  :::column-end:::
  :::column:::
    High
  :::column-end:::
:::row-end:::


> [!IMPORTANT]
> If content is subject to both retention settings and an eDiscovery hold, preserving content for the eDiscovery hold always takes precedence. In this way, the principles of retention expand to eDiscovery holds because they preserve data until an administrator manually releases the hold. However, despite this precedence, organizations shouldn't use eDiscovery holds for long-term data lifecycle management. If you're concerned about automatic deletion of data, you can configure retention settings to retain items forever, or use [disposition review with retention labels](/microsoft-365/compliance/disposition?azure-portal=true).

**Additional reading**. If your organization uses older eDiscovery tools to preserve data, see the following resources:

 -  Exchange:
     -  [In-Place Hold and Litigation Hold](/exchange/security-and-compliance/in-place-and-litigation-holds?azure-portal=true).
     -  [How to identify the type of hold placed on an Exchange Online mailbox](/microsoft-365/compliance/identify-a-hold-on-an-exchange-online-mailbox?azure-portal=true).
 -  SharePoint and OneDrive:
     -  [Add content to a case and place sources on hold in the eDiscovery Center](/SharePoint/governance/add-content-to-a-case-and-place-sources-on-hold-in-the-ediscovery-center?azure-portal=true).
 -  [Retirement of legacy eDiscovery tools](/microsoft-365/compliance/legacy-ediscovery-retirement?azure-portal=true).

### Use retention policies and retention labels instead of older features

For organizations that must proactively retain or delete content in Microsoft 365 for data lifecycle management, it's recommended they use retention policies and retention labels instead of the following older features.

For organizations that currently use these older features, they'll continue to work side by side with Microsoft 365 retention policies and retention labels. However, it's recommended that going forward, they use Microsoft 365 retention policies and retention labels. This best practice enables them to benefit from a single solution to manage both retention and deletion of content across multiple workloads in Microsoft 365.

Older features from Exchange Online:

 -  [Retention tags and retention policies](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies?azure-portal=true), also known as messaging records management (MRM) (deletion only). However, organizations should note the following MRM features aren't currently supported by Microsoft 365 retention policies:
     -  An archive policy for archive mailboxes to automatically move emails from a user's primary mailbox to their archive mailbox after a specified period of time. An archive policy (with any settings) can be used with a Microsoft 365 retention policy that applies to a user's primary and archive mailbox.
     -  Retention policies applied by an admin to specific folders within a mailbox. A Microsoft 365 retention policy applies to all folders in the mailbox. However, an admin can configure different retention settings by using retention labels that a user can apply to folders in Outlook as a [default retention label](/microsoft-365/compliance/create-apply-retention-labels?azure-portal=true).
 -  [Litigation holds](/microsoft-365/compliance/create-a-litigation-hold?azure-portal=true) (retention only). Although Litigation holds are still supported, it's recommended that organizations use Microsoft 365 retention or eDiscovery holds, as appropriate.

Older features from SharePoint and OneDrive:

 -  [Document deletion policies](https://support.office.com/article/Create-a-document-deletion-policy-in-SharePoint-Server-2016-4fe26e19-4849-4eb9-a044-840ab47458ff?azure-portal=true) (deletion only)
 -  [Configuring in place records management](https://support.office.com/article/7707a878-780c-4be6-9cb0-9718ecde050a?azure-portal=true) (retention only)
 -  [Use policies for site closure and deletion](https://support.microsoft.com/en-us/office/use-policies-for-site-closure-and-deletion-a8280d82-27fd-48c5-9adf-8a5431208ba5?azure-portal=true) (deletion only)
 -  [Information management policies](/microsoft-365/compliance/intro-to-info-mgmt-policies?azure-portal=true) (deletion only)

If you've configured SharePoint sites for content type policies or information management policies to retain content for a list or library, those policies are ignored while a retention policy is in effect.
