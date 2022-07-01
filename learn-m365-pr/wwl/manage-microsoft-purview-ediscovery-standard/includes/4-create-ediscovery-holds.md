An organization can use a Microsoft Purview eDiscovery (Standard) case to create holds. Holds preserve content that may be relevant to a case. For example, you can place a hold on:

 -  the Exchange mailboxes and OneDrive for Business accounts of people you're investigating in a case.
 -  the mailboxes and sites that are associated with Microsoft Teams, Microsoft 365 Groups, and Yammer Groups.

> [!NOTE]
> After an organization creates an eDiscovery hold, it may take up to 24 hours for the hold to take effect.

When an organization places content locations on hold, content is preserved until the organization either:

 -  removes the content location from the hold.
 -  deletes the hold.

When an organization creates a hold, it has the following options to scope the content that's preserved in the specified content locations:

 -  **Create an infinite hold where all content in the specified locations is placed on hold**. Alternatively, you can create a query-based hold where only the content in the specified locations that matches a search query is placed on hold.
 -  **Specify a date range to preserve only the content that was sent, received, or created within that date range**. Alternatively, you can hold all content in specified locations regardless of when it was sent, received, or created.

### How to create an eDiscovery hold

Complete the following steps to create an eDiscovery hold that's associated with a eDiscovery (Standard) case:

1.  On the **Microsoft Purview compliance** portal, select **eDiscovery** on the navigation pane. In the **eDiscovery** group, select **Standard**.
2.  On the **eDiscovery (Standard)** page, select the name of the case that you want to create the hold in.
3.  On the detail window for the case, the **Home** tab is displayed by default. Select the **Hold** tab.
4.  On the **Hold** tab, select **+Create**. Doing so initiates the **New Hold** wizard.
5.  In the **New Hold** wizard, on the **Name your hold** page, enter a **Name** for the hold. Optionally add a **Description**, and then select **Next**. The name of the hold must be unique in the organization.
6.  On the **Choose locations** page, select the content locations that you want to place on hold. You can place mailboxes, sites, and public folders on hold.
    
    :::image type="content" source="../media/ediscovery-hold-locations-fe407e4d.png" alt-text="Screenshot of the Choose locations page in the New Hold wizard, with each of the three locations highlighted.":::
    
    
    
    1.  **Exchange mailboxes**. Set the toggle to **On** and then select **Choose users, groups, or teams** to specify the mailboxes to place on hold. Use the search box to find user mailboxes and distribution groups (to place a hold on the mailboxes of group members) to place on hold. You can also place a hold on the associated mailbox for a Microsoft Team, Microsoft 365 Group, and Yammer Group. For more information about the application data that's preserved when a mailbox is placed on hold, see [Content stored in mailboxes for eDiscovery](/microsoft-365/compliance/what-is-stored-in-exo-mailbox?azure-portal=true).
    2.  **SharePoint sites**. Set the toggle to **On** and then select **Choose sites** to specify SharePoint sites and OneDrive accounts to place on hold. Type the URL for each site that you want to place on hold. You can also add the URL for the SharePoint site for a Microsoft Team, Microsoft 365 Group, or a Yammer Group.
    3.  **Exchange public folders**. Set the toggle to **On** to put all public folders in your Exchange Online organization on hold. You can't choose specific public folders to put on hold. Leave the toggle switch **Off** if you don't want to put a hold on public folders.
    
    > [!IMPORTANT]
    > When adding Exchange mailboxes or SharePoint sites to a hold, you must explicitly add at least one content location to the hold. In other words, if you set the toggle to On for mailboxes or sites, you must select specific mailboxes or sites to add to the hold. Otherwise, the eDiscovery hold will be created but no mailboxes or sites will be added to the hold.
7.  When you're done adding locations to the hold, select **Next**.
8.  On the **Query** page, create a query-based hold using keywords or conditions. To do so, complete the following steps.
    
    :::image type="content" source="../media/ediscovery-hold-query-fef6aafb.png" alt-text="Screenshot of the Query page in the New Hold wizard, with the Keywords field and the Add condition option highlighted.":::
    
    
    
    1.  In the box under **Keywords**, type a query to preserve only the content that matches the query criteria. You can specify keywords, email message properties, or site properties, such as file names. You can also use more complex queries that use a Boolean operator, such as AND, OR, or NOT.
    2.  Select **+Add condition** to add one or more conditions to narrow the query for the hold. Each condition adds a clause to the KQL search query that's created and run when you create the hold. For example, you can specify a date range so that email or site documents that were created within the date ranged are preserved. A condition is logically connected to the keyword query (specified in the **Keywords** box) and other conditions by the AND operator. By doing so, items have to satisfy both the keyword query and the condition to be preserved.
    
    For more information about creating a search query and using conditions, see [Keyword queries and search conditions for eDiscovery](/microsoft-365/compliance/keyword-queries-and-search-conditions?azure-portal=true).
9.  After configuring a query-based hold, select **Next**.
10. On the **Review your settings** page, verify the settings are correct. Select the appropriate **Edit** option to edit any setting that requires modification. Once all settings are correct, select **Submit**.

> [!NOTE]
> When you create a query-based hold, all content from selected locations is initially placed on hold. After the hold is created, any content that doesn't match the specified query is cleared from the hold every seven to 14 days. However, a query-based hold won't clear content if more than five holds of any type are applied to a content location, or if any item has indexing issues.

### Query-based holds placed on sites

Organizations should keep in mind the following considerations when they place a query-based eDiscovery hold on documents located in SharePoint sites:

 -  **Preservation of content once a hold is removed**. A query-based hold initially preserves all documents in a site for a short period of time after they're deleted. That means when a document is deleted, it will be moved to the Preservation Hold library even if it doesn't match the criteria of the query-based hold. However, deleted documents that don't match a query-based hold will be removed by a timer job that processes the Preservation Hold library. The timer job runs periodically. It compares all documents in the Preservation Hold library to the organization's query-based eDiscovery holds (and other types of holds and retention policies). The timer job deletes the documents that don't match a query-based hold, but it preserves the documents that do.
 -  **Avoid targeted preservation**. Query-based holds shouldn't be used to perform targeted preservation. For example, preserving documents in a specific folder or site or by using other location-based hold criteria. Doing so may have unintended results. It's recommended that organizations use non-location based hold criteria such as keywords, date ranges, or other document properties to preserve site documents.

### Search locations on eDiscovery hold

When an organization searches for content in a eDiscovery (Standard) case, it can quickly configure the search to only search the content locations that have been placed on a hold associated with the case.

Select the **Locations on hold** option to search all the content locations that have been placed on hold. If the case contains multiple eDiscovery holds, the content locations from all holds will be searched when this option is selected.

Additionally, if a content location was placed on a query-based hold, only the items that match the hold query will be searched when the search is run. In other words, only the content that matches both the hold criteria AND the search criteria is returned with the search results. For example, if a user was placed on query-based case hold that preserves items that were sent or created before a specific date, only those items would be searched. This result is accomplished by connecting the case hold query and the search query by an AND operator.

Organizations should keep in mind the following recommendations when searching locations on eDiscovery hold in the following scenarios:

 -  **A content location is part of multiple holds within the same case**. In this situation, the hold queries are combined by OR operators when you search that content location using the **all case content** option. Similarly, if a content location is part of two different holds, where one is query-based and the other is an infinite hold (where all content is placed on hold), then all content is searched because of the infinite hold.
 -  **A search is configured to search locations on hold and then you change an eDiscovery hold in the case by adding or removing a location, or changing a hold query**. In this scenario, the search configuration is updated with those changes. However, you have to rerun the search after the hold is changed to update the search results.
 -  **Multiple eDiscovery holds are placed on a single location in an eDiscovery case and you select to search locations on hold**. In this situation, the maximum number of keywords for that search query is 500. Why? Because the search combines all the query-based holds by using the OR operator. If there are more than 500 keywords in the combined hold queries and the search query, then all content in the mailbox is searched, not just that content that matches the query-based case holds.
 -  **An eDiscovery hold has a status of On (Pending).** In this scenario, you can still search the locations on hold while the hold is being turned on.

### Removing content locations from an eDiscovery hold

After a mailbox, SharePoint site, or OneDrive account is removed from an eDiscovery hold, a **delay hold** is applied. By doing so, the actual removal of the hold is delayed for 30 days to prevent data from being permanently deleted (purged) from a content location. This delay gives administrators an opportunity to search for or recover content that will be purged after an eDiscovery hold is removed.

The details of how the delay hold works for mailboxes and sites are different.

 -  **Mailboxes**. A delay hold is placed on a mailbox the next time the Managed Folder Assistant processes the mailbox and detects that an eDiscovery hold was removed. Specifically, a delay hold is applied to a mailbox when the Managed Folder Assistant sets one of the following mailbox properties to **True**:
    
    
     -  **DelayHoldApplied**. This property applies to email-related content (generated by people using Outlook and Outlook on the web) that's stored in a user's mailbox.
     -  **DelayReleaseHoldApplied**. This property applies to cloud-based content (generated by non-Outlook apps such as Microsoft Teams, Microsoft Forms, and Microsoft Yammer) that's stored in a user's mailbox. Cloud data generated by a Microsoft app is typically stored in a hidden folder in a user's mailbox.
    
    When a delay hold is placed on the mailbox (when either of the previous properties is set to **True**), the mailbox is still considered to be on hold for an unlimited hold duration, as if the mailbox was on Litigation Hold. After 30 days, the delay hold expires. At that time, Microsoft 365 will automatically attempt to remove the delay hold (by setting the **DelayHoldApplied** or **DelayReleaseHoldApplied** property to **False**) so that the hold is removed. After either of these properties is set to **False**, the corresponding items that are marked for removal are purged the next time the mailbox is processed by the Managed Folder Assistant.
    
    For more information, see [Managing mailboxes on delay hold](/microsoft-365/compliance/identify-a-hold-on-an-exchange-online-mailbox?azure-portal=true).
 -  **SharePoint and OneDrive sites**. Any SharePoint or OneDrive content that's being retained in the Preservation Hold library isn't deleted during the 30-day delay hold period after a site is removed from an eDiscovery hold. This process is similar to what happens when a site is released from a retention policy. Additionally, you can't manually delete this content in the Preservation Hold library during the 30-day delay hold period.
    
    For more information, see [Releasing a policy for retention](/microsoft-365/compliance/retention?azure-portal=true).

A delay hold is also applied to content locations on hold when you close a eDiscovery (Standard) case. Why? Because holds are turned off when a case is closed.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”