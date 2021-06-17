Filtered search permissions can be configured to allow an eDiscovery manager to search only a subset of mailboxes and sites in a Microsoft 365 organization. Additionally, you can also use permissions filtering to allow that same eDiscovery manager to search only for mailbox or site content that meets a specific search criterion. For example, you might let an eDiscovery manager search only the mailboxes and sites of users in a specific location or department.

Search permissions filtering is configured by creating a filter that uses a supported recipient filter to limit which mailboxes can be searched. You can also create filters to specify what mailbox or site content can be searched. When creating these types of filters, you must use a searchable message property.

Search permissions filtering is configured and managed by using the following Security &amp; Compliance Center cmdlets.

:::row:::
  :::column:::
    

**Cmdlet**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

New-ComplianceSecurityFilter


  :::column-end:::
  :::column:::
    

This cmdlet creates a new search permissions filter.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Get-ComplianceSecurityFilters


  :::column-end:::
  :::column:::
    

This cmdlet returns a list of search permissions filters.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Set-ComplianceSecurityFilter


  :::column-end:::
  :::column:::
    

This cmdlet modifies an existing search permissions filter.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Remove-ComplianceSecurityFilter


  :::column-end:::
  :::column:::
    

This cmdlet deletes a search filter.


  :::column-end:::
:::row-end:::


To run the compliance security filter cmdlets, you must:

 -  Be a member of the Organization Management role group in the Security &amp; Compliance Center.
 -  Connect Windows PowerShell to both the Security &amp; Compliance Center and to your Exchange Online organization.

**Additional reading.** For more information, see [Configure permissions filtering for Content Search](/microsoft-365/compliance/permissions-filtering-for-content-search).

The following diagram shows how compliance security filters are used to create compliance boundaries.

:::image type="content" source="../media/compliance-boundaries-in-microsoft-365-4e70eaec.jpg" alt-text="diagram shows how compliance security filters are used to create compliance boundaries.":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”