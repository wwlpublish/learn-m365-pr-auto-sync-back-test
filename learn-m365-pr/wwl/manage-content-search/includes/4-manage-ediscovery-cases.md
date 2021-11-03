To follow regulatory and legal requirements, the features that exist in In-place eDiscovery and eDiscovery cases refer to the same technique of searching through multiple mailboxes, Exchange recipient objects, and even other Microsoft 365 services.

 -  **eDiscovery hold.** This feature is available in Microsoft 365 Compliance center and through the Exchange Management Shell. It’s used to search for certain messaging objects, put them on In-place hold, and process them for further use by exporting them.
 -  **eDiscovery case.** This feature is available in the Microsoft 365 Compliance center and serves the same purpose as eDiscovery hold, but with a different web interface. It also provides the ability to search across all Microsoft 365 services in a single, unified search operation.

> [!NOTE]
> When creating an eDiscovery case in the Microsoft 365 Compliance center, the searches you create are content searches that are only visible from inside the case you created. You can't see those content searches on the Content search page in the Compliance center.

### Differences for eDiscovery in Exchange deployments

When you're working with Exchange Online only or in hybrid deployment, you'll use the more unified eDiscovery search approach and create eDiscovery cases in the Microsoft 365 Compliance Center. This design provides a better search experience by arranging all data in search cases, and search operations can search across all Microsoft 365 services.

> [!CAUTION]
> Organizations with Exchange Server deployments can still run eDiscovery searches with the **New-MailboxSearch** PowerShell cmdlet. However, this cmdlet is no longer available in Exchange Online. In Exchange Online deployments, you must instead use the **New-ComplianceSearch** and **New-CaseHoldPolicy** cmdlets from the Microsoft 365 Compliance center to create new eDiscovery cases.

In a hybrid deployment, some mailboxes exist on the on-premises Exchange Servers, and some mailboxes exist in Exchange Online. An organization with a hybrid deployment can run eDiscovery hold searches on its cloud-based mailboxes using its on-premises EAC. If it intends to copy messages to a discovery mailbox, it must select an on-premises discovery mailbox. Messages from cloud-based mailboxes that are returned in search results are copied to the specified on-premises discovery mailbox.

To successfully run cross-premises eDiscovery searches in an Exchange Server hybrid organization, you must configure OAuth (Open Authorization) authentication between your Exchange on-premises and Exchange Online organizations. OAuth authentication is a server-to-server authentication protocol that allows applications to authenticate to each other. OAuth authentication enables you to use In-Place eDiscovery to search on-premises and cloud-based mailboxes.

OAuth authentication supports the following eDiscovery scenarios in an Exchange hybrid deployment:

 -  Search on-premises mailboxes that use Exchange Online Archiving for cloud-based archive mailboxes.
 -  Search on-premises and cloud-based mailboxes in the same eDiscovery search.

### How eDiscovery works

In-Place eDiscovery uses the content indexes created by Exchange Search. Role-Based Access Control (RBAC) provides the Discovery Management role group to delegate discovery tasks to non-technical personnel, without the need to provide elevated privileges that may allow a user to make any operational changes to Exchange configuration. Both the EAC for Exchange Server and the Microsoft 365 Compliance center for Exchange Online provide an easy-to-use search interface for non-technical personnel, such as legal and compliance officers, records managers, and human resources (HR) professionals.

Authorized users can run an eDiscovery search by selecting the mailboxes and then specifying search criteria, such as:

 -  Keywords
 -  Start and end dates
 -  Sender and recipient addresses
 -  Message types

After the search is complete, authorized users can then select one of the following actions:

 -  **Estimate search results.** This option returns an estimate of the total size and number of items that will be returned by the search based on the criteria you specified.
 -  **Preview search results.** This option provides a preview of the results. Messages returned from each mailbox searched are displayed.
 -  **Copy search results.** This option lets you copy messages to a discovery mailbox.
 -  **Export search results.** After search results are copied to a discovery mailbox, you can export them to a PST file.

### eDiscovery permissions

For authorized users to run In-Place eDiscovery searches, you must add them to one of the following role groups:

 -  In Exchange (core eDiscovery):
    
     -  **Discovery Management.** This role group consists of two management roles: The Mailbox Search Role, which allows a user to run an In-Place eDiscovery search, and the Legal Hold Role, which allows a user to place a mailbox on In-Place hold and Litigation hold.
 -  In the Security &amp; Compliance Center (eDiscovery cases):
    
     -  **eDiscovery Manager**. Members of this role group can create and manage eDiscovery cases. For each case, they can:
        
         -  Add and remove members.
         -  Place content locations on hold.
         -  Create and edit Content Searches associated with the case.
         -  Export the results of a Content Search.
         -  Prepare search results for analysis in Advanced eDiscovery.
     -  **eDiscovery Administrator**. This group can complete all case management tasks that an eDiscovery Manager can do. Additionally, an eDiscovery Administrator can access and manage all eDiscovery cases.
     -  **Reviewer**. This role group has the most restrictive eDiscovery-related permissions. Members of this group can only see and open the list of cases that they're members of in the eDiscovery page of the Microsoft 365 Compliance center. They can't create cases, add members to a case, create holds, create searches, export search results, or prepare results for Advanced eDiscovery. However, members can access cases in Advanced eDiscovery to complete analysis tasks.

By default, permissions to complete In-place eDiscovery-related tasks aren't assigned to any user or messaging administrator. Messaging administrators who are members of the Organization Management role group can add users to the Discovery Management role group and create custom role groups to narrow the scope of a discovery manager to a subset of users. The reason for this is that in most region, administrators can manage the messaging systems and mailboxes, but they can't access any content inside mailboxes.

### Prerequisites and limits to eDiscovery hold

To work with eDiscovery hold in your organization, you must first understand its prerequisites and limitations, including:

 -  eDiscovery hold is available for all Exchange deployments, whether you're using Exchange Standard or Enterprise, Registered Education Savings Plans, Exchange Online Plan 1 licenses, or Exchange Online Plan 2 licenses.
 -  If you need to use eDiscovery hold searches to search for content and to place content on-hold, you must license the In-place hold feature. In-place hold is an Enterprise feature in Exchange Server. For Exchange Online, it requires an Exchange Online Plan 2 license.
 -  In Exchange Server, the resources that In-Place eDiscovery uses are controlled with throttling policies. Some of the relevant default settings are identified in the following chart:

:::row:::
  :::column:::
    **Parameter**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
  :::column:::
    **Default value**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    DiscoveryMaxConcurrency
  :::column-end:::
  :::column:::
    The maximum number of In-Place eDiscovery searches a user can concurrently run.
  :::column-end:::
  :::column:::
    2
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    DiscoveryMaxMailboxes
  :::column-end:::
  :::column:::
    The maximum number of mailboxes that can be searched in a single In-Place eDiscovery search. Public folder mailboxes are also counted against the source mailbox limit.
  :::column-end:::
  :::column:::
    10,000
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    DiscoveryMaxStatsSearchMailboxes
  :::column-end:::
  :::column:::
    The maximum number of mailboxes that can be searched in a single In-Place eDiscovery search that still allows you to view keyword statistics.
  :::column-end:::
  :::column:::
    

100


> [!NOTE]
> After you run an eDiscovery search estimate, you can view keyword statistics. These statistics show details about the number of items returned for each keyword used in the search query. If more than 100 source mailboxes are included in the search, an error is returned if you try to view keyword statistics.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    DiscoveryMaxKeywords
  :::column-end:::
  :::column:::
    The maximum number of keywords that can be specified in a single In-Place eDiscovery search.
  :::column-end:::
  :::column:::
    500
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    DiscoveryMaxSearchResultsPageSize
  :::column-end:::
  :::column:::
    The maximum number of items displayed on a single page when previewing In-Place eDiscovery search results.
  :::column-end:::
  :::column:::
    200
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    DiscoverySearchTimeoutPeriod
  :::column-end:::
  :::column:::
    The number of minutes that an In-Place eDiscovery search will run before timing out.
  :::column-end:::
  :::column:::
    10 minutes
  :::column-end:::
:::row-end:::


 -  There are also limits for creating eDiscovery cases in Exchange Online, including:

| **Description of limit**                                                            | **Limit** |
|:----------------------------------------------------------------------------------- |:---------:|
| Maximum number of cases for an organization.                                        | No limit  |
| Maximum number of case holds for an organization.                                   |  10,000   |
| Maximum number of mailboxes in a single case hold.                                  |   1,000   |
| Maximum number of SharePoint and OneDrive for Business sites in a single case hold. |    100    |

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.