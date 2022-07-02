Electronic discovery, or eDiscovery, is the process of identifying and delivering electronic information that can be used as evidence in legal cases. Organizations can use eDiscovery tools in Microsoft Purview to search for content in:

 -  Exchange Online
 -  SharePoint Online
 -  OneDrive for Business
 -  Microsoft Teams
 -  Microsoft 365 Groups
 -  Yammer teams

Organizations can search mailboxes and sites in the same eDiscovery search, and then export the search results. They can also use Microsoft Purview eDiscovery (Standard) cases to identify, hold, and export content found in mailboxes and sites.

If an organization has an Office 365 E5 or Microsoft 365 E5 subscription (or related E5 add-on subscriptions), it can further manage custodians and analyze content by using the feature-rich Microsoft Purview eDiscovery (Premium) solution in Microsoft 365. eDiscovery (Premium) is explored in greater detail in a later training module.

Microsoft Purview eDiscovery (Standard) builds on the basic search and export functionality of Content search. eDiscovery (Standard):

 -  Enables organizations to create eDiscovery cases and assign eDiscovery managers to specific cases. eDiscovery managers can only access the cases of which they're members.
 -  Lets an organization associate searches and exports with a case.
 -  Lets an organization place an eDiscovery hold on content locations relevant to a case. For example, locations may include Exchange mailboxes, SharePoint sites, OneDrive accounts, and Microsoft Teams.

### Explore the eDiscovery (Standard) workflow

The following diagram displays the basic workflow on how to get started using eDiscovery (Standard).

:::image type="content" source="../media/core-ediscovery-workflow-c44de18f.png" alt-text="Diagram showing the basic workflow steps when implementing Microsoft Purview eDiscovery Standard.":::


Organizations must create eDiscovery holds for people of interest, search for content that's relevant to its investigation, and then export that data for further review.

1.  **Create an eDiscovery hold**. The first step after creating a case is placing a hold (also called an **eDiscovery hold**) on the content locations of the people of interest in the investigation. Content locations include Exchange mailboxes, SharePoint sites, OneDrive accounts, and the mailboxes and sites associated with Microsoft Teams and Microsoft 365 Groups.
    
    > [!NOTE]
    > While this step is optional, creating an eDiscovery hold preserves content that may be relevant to the case during the investigation.
    
    When an organization creates an eDiscovery hold, it can either:
    
    
     -  Preserve all content in specific content locations.
     -  Create a query-based hold to preserve only the content that matches a hold query.
    
    Besides preserving content, another good reason to create eDiscovery holds is to quickly search the content locations on hold (instead of having to select each location to search) when you create and run searches in the next step. After an organization completes its investigation, it can release any hold that it created.
2.  **Search for content**. After an organization creates eDiscovery holds, it can use the built-in search tool to search the content locations on hold. It can also search other content locations for data that may be relevant to the case.
    
    An organization can create and run different searches that are associated with its case. It can use keywords, properties, and conditions to build search queries that return search results with the data that's most likely relevant to the case.
    
    An organization can also:
    
    
     -  View search statistics that may help it refine a search query to narrow the results.
     -  Preview the search results to quickly verify whether the relevant data is being found.
     -  Revise a query and rerun the search.
3.  **Export and download search results**. After an organization searches for and finds data that's relevant to its investigation, it can export the data out of Microsoft 365 for review by people outside of the investigation team. Exporting data is a two-step process:
    
    
    1.  **Export the results of a search out of Microsoft 365**. This step is accomplished by copying the results of a search to a Microsoft-provided Azure Storage location.
    2.  **Download the exported data**. Use the eDiscovery Export tool to download the exported content to a local computer. Besides the exported data files, the export package contains an export report, a summary report, and an error report.

Each of these steps will be examined in greater detail in the upcoming units in this module.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”