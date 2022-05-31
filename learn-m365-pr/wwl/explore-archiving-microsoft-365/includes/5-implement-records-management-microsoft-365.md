Organizations of all types require a records management solution to manage regulatory, legal, and business-critical records across their corporate data. Records management for Microsoft Purview:

 -  Helps an organization manage their legal obligations.
 -  Demonstrates compliance with regulations.
 -  Increases efficiency with regular disposition of items that are:
     -  no longer required to be retained.
     -  no longer of value.
     -  no longer required for business purposes.

Organizations can use the following capabilities to support their records management solution for Microsoft 365 services and apps:

 -  Label content as a record. Create and configure retention labels to mark content as a [record](/microsoft-365/compliance/records-management?azure-portal=true). Labels can then be applied by users or automatically applied by identifying sensitive information, keywords, or content types.
 -  Migrate and manage your retention requirements with file plan. By using a [file plan](/microsoft-365/compliance/file-plan-manager?azure-portal=true), you can bring in an existing retention plan to Microsoft 365, or build a new one for enhanced management capabilities.
 -  Configure retention and deletion settings with retention labels. Configure [retention labels](/microsoft-365/compliance/retention?azure-portal=true) with the retention periods and actions based on various factors that include the date last modified or created.
 -  Start different retention periods when an event occurs with [event-based retention](/microsoft-365/compliance/event-driven-retention?azure-portal=true).
 -  Review and validate disposition with [disposition reviews](/microsoft-365/compliance/disposition?azure-portal=true) and proof of [records deletion](/microsoft-365/compliance/disposition?azure-portal=true#disposition-of-records?azure-portal=true).
 -  Export information about all disposed items with the [export option](/microsoft-365/compliance/disposition?azure-portal=true#filter-and-export-the-views?azure-portal=true).
 -  Set specific permissions for records manager functions in your organization to [have the right access](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center?azure-portal=true).

An organization can use these capabilities to incorporate its retention schedules and requirements into a records management solution. The organization can then manage retention, records declaration, and disposition to support the full lifecycle of its content.

**Additional resource**. You may find it useful to download this [records management FAQ document](https://aka.ms/MIPC/Blog-RecordsManagementWebinar?azure-portal=true).

### What's a record?

When content is declared a record:

 -  Restrictions are placed on the items in terms of what [actions are allowed or blocked](/microsoft-365/compliance/records-management?azure-portal=true#compare-restrictions-for-what-actions-are-allowed-or-blocked?azure-portal=true).
 -  Other activities about the item are logged.
 -  You have proof of disposition when the items are deleted at the end of their retention period.

Retention labels are used to mark content as either a record or a regulatory record. The difference between these two record types is explained in the next section. You can either:

 -  Publish those labels so that users and administrators can manually apply them to content.
 -  Auto-apply those labels to content that you want to mark as a record or a regulatory record.

By using retention labels to declare records, you can implement a single and consistent strategy for managing records across your Microsoft 365 environment.

### Enable the regulatory record option

By default, the retention label option to mark content as a regulatory record isn't displayed in the retention label wizard. To display this option, you must first run a PowerShell command:

1.  [Connect to Security &amp; Compliance Center PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).
2.  Run the following command:
    
    ```powershell
    Set-RegulatoryComplianceUI -Enabled $true
    ```
    
    > [!NOTE]
    > There is no prompt to confirm this change. The update to this setting takes effect immediately.

If you change your mind about seeing this option in the retention label wizard, you can hide it again by running the same command with the false value:

```powershell
Set-RegulatoryComplianceUI -Enabled $false
```

### Configure retention labels to declare records

When you create a retention label from the Records Management solution in the Microsoft Purview compliance portal, you have the option to mark items as a record. If you ran the PowerShell command from the previous section, you can alternatively mark an item as a regulatory record, as seen in the following screenshot.

:::image type="content" source="../media/declare-records-b2a02c83.png" alt-text="Screenshot of records management in the Microsoft Purview compliance center and the option to declare content as a record or regulatory record.":::


Using this retention label, you can now apply it to SharePoint or OneDrive documents and Exchange emails, as needed.

### Compare restrictions for what actions are allowed or blocked

The following table identifies what restrictions are placed on content as a result of applying a standard retention label. It also identifies retention labels that mark content as a record or regulatory record.

A standard retention label has retention settings and actions. However, it doesn't mark content as a record or a regulatory record.

> [!NOTE]
> For completeness, the table includes columns for a locked and unlocked record. These record types are applicable to SharePoint and OneDrive, but not Exchange. The ability to lock and unlock a record uses [record versioning](/microsoft-365/compliance/record-versioning?azure-portal=true) that isn't supported for Exchange items. So for all Exchange items that are marked as a record, the behavior maps to the **Record - locked** column, and the **Record - unlocked** column isn't relevant.

:::row:::
  :::column:::
    **Action**
  :::column-end:::
  :::column:::
    **Retention label**
  :::column-end:::
  :::column:::
    **Record - locked**
  :::column-end:::
  :::column:::
    **Record - unlocked**
  :::column-end:::
  :::column:::
    **Regulatory record**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Edit contents
  :::column-end:::
  :::column:::
    Allowed
  :::column-end:::
  :::column:::
    Blocked
  :::column-end:::
  :::column:::
    Allowed
  :::column-end:::
  :::column:::
    Blocked
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Edit properties, including rename
  :::column-end:::
  :::column:::
    Allowed
  :::column-end:::
  :::column:::
    Allowed (1)
  :::column-end:::
  :::column:::
    Allowed
  :::column-end:::
  :::column:::
    Blocked
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Delete
  :::column-end:::
  :::column:::
    Allowed (2)
  :::column-end:::
  :::column:::
    Blocked
  :::column-end:::
  :::column:::
    Blocked
  :::column-end:::
  :::column:::
    Blocked
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Copy
  :::column-end:::
  :::column:::
    Allowed
  :::column-end:::
  :::column:::
    Allowed
  :::column-end:::
  :::column:::
    Allowed
  :::column-end:::
  :::column:::
    Allowed
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Move within container (3)
  :::column-end:::
  :::column:::
    Allowed
  :::column-end:::
  :::column:::
    Allowed
  :::column-end:::
  :::column:::
    Allowed
  :::column-end:::
  :::column:::
    Allowed
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Move across containers (3)
  :::column-end:::
  :::column:::
    Allowed
  :::column-end:::
  :::column:::
    Allowed if never unlocked
  :::column-end:::
  :::column:::
    Blocked
  :::column-end:::
  :::column:::
    Blocked
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Open/Read
  :::column-end:::
  :::column:::
    Allowed
  :::column-end:::
  :::column:::
    Allowed
  :::column-end:::
  :::column:::
    Allowed
  :::column-end:::
  :::column:::
    Allowed
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Change label
  :::column-end:::
  :::column:::
    Allowed
  :::column-end:::
  :::column:::
    Allowed - container admin only
  :::column-end:::
  :::column:::
    Blocked
  :::column-end:::
  :::column:::
    Blocked
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Remove label
  :::column-end:::
  :::column:::
    Allowed
  :::column-end:::
  :::column:::
    Allowed - container admin only
  :::column-end:::
  :::column:::
    Blocked
  :::column-end:::
  :::column:::
    Blocked
  :::column-end:::
:::row-end:::


**Footnotes:**

1. Editing properties for a locked record is allowed by default but can be blocked by a tenant setting in the Microsoft Purview compliance portal. Navigate to **Records management &gt; Records management settings &gt; Retention labels &gt; Allow editing of record properties**.

2. Deleting labeled items in SharePoint and OneDrive can be blocked as a tenant setting in the **Microsoft Purview compliance** portal. Navigate to **Records management &gt; Records management settings &gt; Retention labels &gt; Deletion of items**.

When you apply a retention label to a list item that has a document attachment, that document doesn't inherit the retention settings. The document can also be deleted from the list item. In comparison, if that list item was declared a record with a retention label, the document attachment would inherit the retention settings and couldn't be deleted.

3. Containers include SharePoint document libraries, OneDrive accounts, and Exchange mailboxes.

### Record restrictions

The most important difference for a regulatory record is that after it's applied to content, nobody, not even a global administrator, can remove the label. Retention labels configured for regulatory records also have the following admin restrictions:

 -  The retention period can't be made shorter after the label is saved, only extended.
 -  These labels aren't supported by auto-labeling policies, and must be applied by using [retention label policies](/microsoft-365/compliance/create-apply-retention-labels?azure-portal=true).

In addition, a regulatory label can't be applied to a document that's checked out in SharePoint.

Because of the restrictions and irreversible actions, an organization should ensure that it really does need to use regulatory records before it select this option for its retention labels. To help prevent accidental configuration, this option isn't available by default. Instead, it must first be enabled by using PowerShell. Instructions on how to complete this task are included in [Declare records by using retention labels](/microsoft-365/compliance/declare-records?azure-portal=true).
