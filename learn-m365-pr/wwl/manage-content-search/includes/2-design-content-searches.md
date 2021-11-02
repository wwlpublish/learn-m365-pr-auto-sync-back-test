Content searches are a basic part of eDiscovery in both on-premises and web-based implementations. However, content searches in web-based implementations are much more powerful as they can search across all Microsoft 365 services. Search performance is fast with few limitations, which makes it ideal for quick and large search operations.

There are several situations where a simple and fast search operation is useful. For example, if you need to bulk delete certain emails or other potentially harmful or high-risk messages from different mailboxes.

You must be a member of the eDiscovery Manager role group in the Microsoft 365 Defender portal to run searches and to preview and export search results in the Content Search page. You don't have to assign other search permissions in Exchange Online.

> [!WARNING]
> You must be careful when assigning the eDiscover Manager role group. This role provides permission to the powerful “search and purge” feature, which allows the user to delete email messages from all mailboxes in your organization. This feature is examined more closely in the next section.

### Limitations for Content Search

Content Search isn't limited in the number of mailboxes it can search, nor is there a limit in the number of concurrent searches that can be run in your organization. However, a single user can only run up to 10 searches at the same time. While there's also various limitations for the preview of your search results, those limits only apply when previewing search results before the results are exported.

A Content Search that also deletes items is known as a “search and purge.” This type of search, which is limited to 50,000 mailboxes, is accomplished by using the **New-ComplianceSearchAction -Purge** command. The purge action will fail if a Content Search that includes a purge action is run on more than 50,000 mailboxes.

> [!CAUTION]
> A single user can start up to 10 searches simultaneously. This limit is often reached when the user tries to start multiple searches by using the **Get-ComplianceSearch** \| **Start-ComplianceSearch** command in the Security &amp; Compliance Center PowerShell. Keep this limitation in mind when planning content searches.

### Plan cloud-based mailbox searches for on-premises users

If your organization has an Exchange hybrid deployment and has enabled Microsoft Teams, users can use the Teams' chat application for instant messaging.

 -  For both cloud-based and on-premises users, the Teams' chat data (also called 1xN chats) is saved to the user’s primary mailbox.
 -  For cloud-based users, their primary mailbox is in the cloud.
 -  For on-premises users, their primary mailbox is stored on-premises.

This dual location of primary mailboxes originally limited searches of Teams' chat data to cloud-based users only because the Content Search tool in the Microsoft 365 Compliance center only targets cloud-based mailboxes. However, Microsoft 365 addressed this limitation by including a cloud-based storage area (called a cloud-based mailbox for on-premises users) to store Teams' chat data for on-premises users. This design lets you use the Content Search tool in the Microsoft 365 Compliance center to search and export Teams' chat data for both on-premises and cloud-based users.

Messaging administrators must consider the following items when setting up and searching cloud-based mailboxes for on-premises users:

 -  The user accounts in your on-premises directory service (such as Active Directory) must be synchronized with Azure Active Directory, which is the directory service in Microsoft 365. This design means that a mail user account is created in Microsoft 365 for each user whose primary mailbox is in the on-premises organization.
 -  The cloud-based mailbox for on-premises users is only used to store Teams' chat data. An on-premises user can't sign into the cloud-based mailbox or access it in any way. For example, it can't be used to send or receive email messages.
 -  Placing a cloud-based mailbox for an on-premises user on a hold associated with an eDiscovery case or assigning it to a Microsoft 365 retention policy isn't supported.
 -  The content location picker for eDiscovery holds displays on-premises users and will let you select them, even though an eDiscovery hold can't be applied to the cloud-based mailboxes for selected on-premises users.
 -  For an organization to search for Teams' chat data in the cloud-based mailboxes of its on-premises users, the organization must submit a request to Microsoft Support.

> [!NOTE]
> Teams channel conversations are always stored in the cloud-based mailbox that's associated with the Team. This design enables organizations to use Content Search to search channel conversations without having to file a support request.

Teams' chat data is indexed for search after it’s stored in the cloud-based mailbox. This design lets you use Content Search (and searches associated with eDiscovery cases) to search, preview, and export Teams' chat data for on-premises users. You can also use the **ComplianceSearch** cmdlets in the Microsoft 365 Compliance Center PowerShell to search for Teams' chat data for on-premises users.

The following graphic shows the workflow of how Teams' chat data for on-premises users is made available for search, preview, and export.

:::image type="content" source="../media/teams-content-search-aee266c2.png" alt-text="Graphic shows the workflow of how Teams' chat data for on-premises users is made available for search, preview, and export.":::


### Content Search considerations

Consider the following questions when designing a Content Search:

 -  Who should create and run the Content Search?
 -  What type of Content Search do you want to create (for example, New search, Guided search, or Search by ID list)?
 -  What keywords should be used for the search?
 -  What conditions should be used (for example, type of data, sender, date, subject, and so on)?
 -  Do you want to search all locations, or only specific locations (for example, Exchange Online, SharePoint Online, Microsoft Teams, and so on)?
 -  Which action, if any, should be performed on the items that are found (for example, soft delete, purge, and so on)?

Content Search is useful when you need to run large searches. It's also useful when you simply need to search for specific data in your organization without needing to apply an eDiscovery Hold on the content or create an eDiscovery case.

After you run a Content Search, the number of content locations and an estimated number of search results are displayed in the details pane on the Content Search page in the Microsoft 365 Compliance center. After you run a Content Search, you can:

 -  Preview the results.
 -  Export the results to a local computer.
 -  Prepare the results for analysis.

**Additional reading**. For more information, see [Limits for Content Search in the Microsoft 365 Compliance Center](/microsoft-365/compliance/limits-for-content-search?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.