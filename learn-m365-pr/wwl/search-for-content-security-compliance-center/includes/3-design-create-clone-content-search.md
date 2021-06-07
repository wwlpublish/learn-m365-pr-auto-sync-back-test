Running a content search typically incorporates the following tasks:

 -  **Design a Content search.** Designing a search includes defining its structure and purpose.<br>
 -  **Create a Content search.** Use the Content search tool to quickly find email, documents, and instant messaging conversations.
 -  **Clone a Content search (optional).** Cloning a Content search can be used to break up a large, single search into multiple, smaller searches that run more quickly.
 -  **Search for and delete email (if necessary).** Organizations must sometimes find and delete harmful or high-risk emails. For example, when a large number of users receive a phishing attack email message that must be deleted immediately.

This unit examines each of these tasks.

### Design a Content search

Consider the following questions when designing a Content search:

 -  Who should create and run the Content search?
 -  What type of Content search do you want to create (for example, New search, Guided search, Search by ID list, and so on)?
 -  What keywords should be used for the search?
 -  What conditions should be used (for example, type of data, sender, date, subject, and so on)?
 -  Do you want to search all locations, or only specific locations (for example, SharePoint, Microsoft Teams, and son on)?

When planning your search, consider the limits of Content search in the Microsoft 365 compliance center. Once you understand the options that are available for a Content search, you can continue and create the search.

### Create a Content Search

As mentioned in the previous unit, you must be a member of the eDiscovery Manager role group in the Security &amp; Compliance Center to have the necessary permissions to create a Content Search. The following steps must be completed to create a search:

1.  Go to the Microsoft 365 compliance center and sign in using the credentials of an account that's been assigned the appropriate permissions.
2.  In the left-hand navigation pane of the Microsoft 365 compliance center, select **Show all**, and then select **Content search**.
3.  On the **Content search** page, select **New search**.

> [!NOTE]
> The **Search by ID list** option enables organizations to search for specific email messages and other mailbox items using a list of Exchange IDs. To create an ID list search, you submit a comma-separated value (CSV) file that identifies the specific mailbox items to search for. For instructions, see [Prepare a CSV file for an ID list search](/microsoft-365/compliance/csv-file-for-an-id-list-content-search).

4.  Type a name for the search, an optional description that helps identify the search. The name of the search must be unique in your organization.
5.  On the **Locations** page, choose the content locations that you want to search. The four locations available on this page are shown in the following image as items A, B, C, and D. These items are described in detail following the image.
    
    :::image type="content" source="../media/content-search-locations-7c1a4776.png" alt-text="screenshot showing the Locations page and the four locations available, including Exchange mailboxes, SharePoint sites, Exchange public folders, and the Add App Content for On-Premises Users checkbox":::
    

    **A. Exchange mailboxes.** Set the toggle to **On** and then select **Choose users, groups, or teams** to specify the mailboxes to place on hold. Use the search box to find user mailboxes and distribution groups (to place a hold on the mailboxes of group members) to place on hold. You can also search the mailbox associated with a Microsoft Team (for channel messages), Office 365 Group, and Yammer Group. For more information about the application data stored in mailboxes, see [Content stored in mailboxes for eDiscovery](/microsoft-365/compliance/what-is-stored-in-exo-mailbox).

    **B. SharePoint sites.** Set the toggle to **On** and then select **Choose sites** to specify SharePoint sites and OneDrive accounts to place on hold. Type the URL for each site that you want to place on hold. You can also add the URL for the SharePoint site for a Microsoft Team, Office 365 Group, or Yammer Group.

    **C. Exchange public folders.** Set the toggle to **On** to put all public folders in your Exchange Online organization on hold. You can't choose specific public folders to put on hold. Leave the toggle switch **Off** if you don't want to put a hold on public folders.

    **D. Add App Content for On-Premises Users.** Keep this checkbox selected to search for Teams content for on-premises users. If you search all Exchange mailboxes in the organization and this checkbox is selected, the cloud-based storage used to store Teams chat data for on-premises users will be included in the scope of the search. For more information, see [Search for Teams chat data for on-premises users](/microsoft-365/compliance/search-cloud-based-mailboxes-for-on-premises-users).

6.  On the **Define your search conditions** page, type a keyword query and add conditions to the search query if necessary. The three parameters available on this page are shown in the following image as items A, B, and C. These items are described in detail following the image.
    
    :::image type="content" source="../media/content-search-conditions-4edb95a9.png" alt-text="screenshot of the content search conditions page with the three search parameters for entering keywords, showing the keyword list, and adding conditions":::
    

    **A. Enter keywords.** Specify keywords, message properties such as sent and received dates, or document properties such as file names or the date that a document was last changed. You can use more complex queries that use a Boolean operator, such as AND, OR, NOT, and NEAR. If you leave the keyword box empty, all content located in the specified content locations is included in the search results. For more information, see [Keyword queries and search conditions for eDiscovery](/microsoft-365/compliance/keyword-queries-and-search-conditions).

    **B. Show keyword list.** You can optionally select the **Show keyword list** checkbox and the type a keyword in each row. By doing so, the keywords on each row are connected by a logical operator (c:s) that is similar in functionality to the OR operator in the search query that's created.

    Using the keyword list enables you to get statistics that show how many items match each keyword. These statistics can help quickly identify which keywords are the most (and least) effective. You can also use a keyword phrase (surrounded by parentheses) in a row. For more information about the keyword list and search statistics, see [Get keyword statistics for searches](/microsoft-365/compliance/view-keyword-statistics-for-content-search).

> [!NOTE]
> To help reduce issues caused by large keyword lists, you're limited to a maximum of 20 rows in the keyword list.

    **C. Add condition.** You can add search conditions to narrow a search and return a more refined set of results. Each condition adds a clause to the search query that is created and run when you start the search. A condition is logically connected to the keyword query (specified in the keyword box) by a logical operator (c:c) that is similar in functionality to the AND operator. That means that items have to satisfy both the keyword query and one or more conditions to be included in the results. This design is how conditions help to narrow your results. For a list and description of conditions that you can use in a search query, see [Search conditions](/microsoft-365/compliance/keyword-queries-and-search-conditions).

7.  Review the search settings and edit them, if necessary. Then submit the search to start it.

> [!TIP]
> To access this content search again or access other content searches listed on the Content search page, select the search and then select **Open**.

### Clone a Content search

Although enhanced by scalability and performance improvements, searching a large number of mailboxes or SharePoint sites when using Content Search may still take a while to complete. Cloning a Content Search can be used to break up a large, single search into multiple, smaller searches that run more quickly.

Creating a Content Search in the Microsoft 365 compliance center that searches many mailboxes or SharePoint and OneDrive for Business sites may take a while. Specifying the sites to search can also be prone to errors if you mistype a URL. To avoid these issues, you can create a Windows PowerShell script to quickly clone an existing Content Search.

When you clone a search, a new search (with a different name) is created that contains the same properties as the original search. Then you can edit the new search by changing the keyword query or the date range, and run it.

Cloning a Content Search may also be advantageous when you need to:

 -  Compare the results of different keyword search queries run on the same content locations.
 -  Reenter a large number of content locations when creating a new search, thereby saving time and effort.
 -  Reduce the size of the search results. For example, if you have a search that returns too many results to export, you can clone the search and then add a search condition based on a date range to reduce the number of search results.

Microsoft provides a sample of a script that you can run to clone a Content Search. This sample script appears in the following resource: [Clone a Content Search](/microsoft-365/compliance/clone-a-content-search). This article includes:

 -  A list of prerequisites to running the script.
 -  A copy of the script itself.
 -  Instruction on editing and running the script.
 -  A disclaimer from Microsoft that the script is provided AS IS without warranty of any kind.

Once you run the script to create the clone, you can edit and run the new search in the Microsoft 365 compliance center.

### Searching for and deleting email messages

Occasionally, you may need to find and remove potentially harmful or high-risk email such as:

 -  Messages that contain a dangerous attachment or virus.
 -  Phishing messages.
 -  Messages that contain sensitive data.

You can use Content Search to search for and delete email messages from all the mailboxes in your organization.

The first step is to create and run a Content Search to find the messages that you want to remove from mailboxes in your organization. You can create the search by using the Content Search feature in the Microsoft 365 compliance center, or by running the **New-ComplianceSearch** and **Start-ComplianceSearch** cmdlets. The messages that match the query for this search are deleted by running the **New-ComplianceSearchAction** cmdlet.

> [!IMPORTANT]
> When you run the **New-ComplianceSearchAction** cmdlet, the content locations that are searched in the Content Search can't include SharePoint or OneDrive for Business sites. If they do, an error occurs. You can only include mailboxes and public folders in a Content Search that's used to delete email messages.

After you've created and refined a Content Search to return the messages that you want to remove, you must then delete the messages. To do so, you must connect to the Microsoft 365 compliance center with remote PowerShell and then run the **New-ComplianceSearchAction** cmdlet. Running this cmdlet will delete the messages, which are moved to the associated users' Recoverable Items folder.

**Additional reading.** For more information, see [Search for and delete email messages in your Microsoft 365 organization](/microsoft-365/compliance/search-for-and-delete-messages-in-your-organization).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”