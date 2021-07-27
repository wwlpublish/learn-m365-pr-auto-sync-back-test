In this unit, you'll learn what eDiscovery is and how it is implemented in Exchange Online. You'll see how you can apply an eDiscovery role-based access control to the compliance team.

## What is eDiscovery?

Microsoft 365 provides eDiscovery, or Electronic discovery, to help you identify and deliver electronic information that can be used as evidence in legal cases. You can use eDiscovery in Microsoft 365 to search for content in Exchange Online mailboxes, Microsoft 365 Groups, Microsoft Teams, SharePoint Online and OneDrive for Business sites, Skype for Business conversations, and Yammer teams. You can search for mailboxes and sites in the same eDiscovery search by using the Content Search tool in the Microsoft 365 Defender portal. And you can use eDiscovery cases in the Microsoft 365 Defender portal to identify, hold, and export content found in mailboxes and sites.

## Permissions and role groups

Before your users can use any of the eDiscovery-related tools in the Microsoft 365 Defender portal in Office 365 or the Microsoft 365 compliance center, you have to assign them the appropriate permissions. The easiest way to do this is to add the person the appropriate role group on the **Permissions** page in the Microsoft 365 Defender portal.

The primary eDiscovery-related role group in the Microsoft 365 Defender portal is called **eDiscovery Manager**. There are two subgroups within this role group.

- **eDiscovery Managers** - An eDiscovery Manager can search content locations in the organization, and perform search-related actions like preview and export search results. They can also create and manage eDiscovery cases and Advanced eDiscovery cases. eDiscovery Managers can only access and manage the cases they create. They can't access or manage cases created by other eDiscovery Managers.
- **eDiscovery Administrators** - An eDiscovery Administrator is a member of the eDiscovery Manager role group, and can perform the same content search and case management-related tasks that an eDiscovery Manager can perform. Additionally, an eDiscovery Administrator can:
  - Access all cases in the Microsoft 365 Defender portal, not just the cases they create.
  - Access case data in Advanced eDiscovery for any case in the organization.
  - Manage any eDiscovery case after they add themselves as a member of the case.

## RBAC roles in the Microsoft 365 Defender portal

The following eDiscovery-related RBAC roles are available in the Microsoft 365 Defender portal:

- **Case Management** - create, edit, delete, and control access to eDiscovery and Advanced eDiscovery cases in the Microsoft 365 Defender portal.
- **Compliance Search** - run the Content Search tool in the Microsoft 365 Defender portal. This role allows a user to get an estimate of the search results and create export reports. However, additional roles are needed to initiate content search actions such as previewing, exporting, or deleting search results.
- **Export** - export the results of a Content Search to a local computer. It also allows users to prepare search results for analysis in Advanced eDiscovery.
- **Hold** - place content on hold in mailboxes, public folders, sites, conversations, and groups. When content is on hold, content owners can still modify or delete the original content, but the content will be preserved until the hold is removed or until the hold duration expires.
- **Preview** - view a list of items that were returned from a Content Search. They can also open and view each item from the list to view its contents.
- **Review** - access case data in Advanced eDiscovery (classic) (also known as Advanced eDiscovery v1). This role doesn't allow the user to preview the results of a content search that's associated with the case or do other content search or case management tasks.
- **RMS Decrypt** - decrypt rights-protected email messages when exporting search results or preparing search results for analysis in Advanced eDiscovery.
- **Search and purge** - perform bulk removal of data matching the criteria of a content search.

You can see more information about RBAC roles and how the work in eDiscovery in [RBAC roles related to eDiscovery](/microsoft-365/compliance/assign-ediscovery-permissions?rbac-roles-related-to-ediscovery).
