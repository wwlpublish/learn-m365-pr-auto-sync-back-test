eDiscovery is the process of identifying and delivering electronic information that can be used as evidence in legal cases. Large Enterprises are often exposed to high penalty legal proceedings that demand submission of all Electronically Stored Information (ESI). Microsoft Teams content can be searched and used during eDiscovery investigations.

## Teams content location for eDiscovery
You can use eDiscovery tools to search for Teams content. Depends on the type of Teams content, you will configure different locations in eDiscovery.  

|Teams content | Content location|
|--|--|
|Microsoft Teams 1:1 or group chats| Users' mailboxes|
|Standard channel messages| Group mailbox representing the team|
|Private channel messages| Private channel members' mailbox|
|Files uploaded in standard channels|SharePoint site used by the team|
|Files uploaded in private channels|SharePoint site used by the channel|
|Private Content| Users' OneDrive|
 
> [!NOTE]
> Placing a user on hold does not automatically place a group on hold or vice-versa.

## eDiscovery solutions

There are three key capabilities of eDiscovery.

:::image type="content" source="../media/m365-ediscovery-solution-graphic.png" alt-text="Key capabilities of Microsoft 365 eDiscovery tools":::

- **Content search**. Use use the Content search tool to search for content across Microsoft 365 data sources and then export the search results to local computer.

- **Core eDiscovery**. Core eDiscovery builds on the basic search and export functionality of Content search. You can create eDiscovery cases and eDiscovery managers who can only access the case their members of. Core eDiscovery lets you associate searches and exports with a case and allows you to place an eDiscovery hold on content locations relevant to the case.

- **Advanced eDiscovery**. The Advanced eDiscovery tool builds on the existing case management, preservation, search, and export capabilities in Core eDiscovery. Advanced eDiscovery provides an end-to-end workflow to identify, preserve, collect, review, analyze, and export content that's responsive to your organization's internal and external investigations. It lets legal teams manage custodians and the legal hold notification workflow to communicate with custodians involved in a case. 

To get you started using core eDiscovery, here's a simple workflow of creating eDiscovery holds for people of interest, searching for content that relevant to your investigation, and then exporting that data for further review. 

:::image type="content" source="../media/core-ediscovery-workflow.png" alt-text="Core eDiscovery workflow":::


## eDiscovery permissions

If you want people to use any of the eDiscovery-related tools in the Microsoft 365 compliance center, you have to assign them the appropriate permissions. The easiest way to do this is to add the person the appropriate role group on the **Permissions** page in the compliance center. 

The primary eDiscovery-related role group in Microsoft 365 compliance center is called **eDiscovery Manager**. There are two subgroups within this role group.
 
- **eDiscovery Managers**. An eDiscovery Manager can use eDiscovery search tools to search content locations in the organization, and perform various search-related actions such as preview and export search results. Members can also create and manage cases in Core eDiscovery and Advanced eDiscovery, add, and remove members to a case, create case holds, run searches associated with a case, and access case data. eDiscovery Managers can only access and manage the cases they create. They can't access or manage cases created by other eDiscovery Managers.
  
- **eDiscovery Administrators**. An eDiscovery Administrator is a member of the eDiscovery Manager role group, and can perform the same content search and case management-related tasks that an eDiscovery Manager can perform. Additionally, an eDiscovery Administrator can:
  
  - Access all cases that are listed on the **Core eDiscovery** and **Advanced eDiscovery** pages in the Microsoft 365 compliance center.

  - Access case data in Advanced eDiscovery for any case in the organization.
  
  - Manage any eDiscovery case after they add themselves as a member of the case.
 

## Create a Core eDiscovery case

Do the following to create a case and start using Core eDiscovery.

1. From the [Microsoft 365 compliance center](https://compliance.microsoft.com/?azure-portal=true), select **eDiscovery** > **Core**.

2. On the Core eDiscovery page, select **+ Create a case**.

3. On the New case pane on the right side, enter a meaningful **Case name** and a **Case description** that tells the purpose of this case. Then select **Save**. 

The case that you created will now be displayed in the list of cases on the **eDiscovery** page, and it's ready to add holds and searches.
 
## Create an eDiscovery hold for Teams content

You can use a Core eDiscovery case to create holds to preserve content that might be relevant to the case. To create an eDiscovery hold that's associated with a Core eDiscovery case:
 
1. From the [Microsoft 365 compliance center](https://compliance.microsoft.com/?azure-portal=true), select **eDiscovery** > **Core**.
2. On the **Core eDiscovery** page, select the name of the case that you want to create the hold in. 
3. On the Home page for the case, select the **Holds** tab.  
4. Select **+ Create** to create a new hold.
5. On the Name your hold page, enter a meaningful **Name** and a **Description**, that explains the purpose of this hold.

6. Select **Next**.  
7. On the Choose locations page, you can decide to hold individual locations:

   * **Exchange mailboxes**. Set the toggle to **On** and then select **Choose users, groups, or teams** to specify the mailboxes to place on hold. 

   * **SharePoint sites**. Set the toggle to **On** and then select **Choose sites** to specify SharePoint sites and OneDrive accounts to place on hold. 
  
   * **Exchange public folders**. Set the toggle to **On** to put all public folders in your Exchange Online organization on hold.

		:::image type="content" source="../media/ediscovery-hold-locations.png" alt-text="Choose the content locations to place on hold":::

8. When you're done adding locations to the hold, select **Next**.

9. To create a query-based hold using keywords or conditions, complete the following steps. To preserve all content in the specified content locations, select **Next**.

    1. In the box under **Keywords**, type a query to preserve only the content that matches the query criteria. You can specify keywords, email message properties, or site properties, such as file names. You can also use more complex queries that use a Boolean operator, such as **AND**, **OR**, or **NOT**.

    2. Select **Add condition** to add one or more conditions to narrow the query for the hold. Each condition adds a clause to the KQL search query that is created and run when you create the hold. For example, you can specify a date range so that email or site documents that were created within the date ranged are preserved. A condition is logically connected to the keyword query (specified in the **Keywords** box) and other conditions by the **AND** operator. That means items have to satisfy both the keyword query and the condition to be preserved.

10. After configuring a query-based hold, select **Next**.

11. Review your settings (and edit them if necessary), and then select **Submit**.

 
> [!NOTE]
> After placing a content location on hold, it can take up to 24 hours for the hold to become active.

## Search for content in a case
After a Core eDiscovery case is created and people of interest in the case are placed on hold, you can create and run one or more searches for content relevant to the case. 

To create a Core eDiscovery search:

1. From the [Microsoft 365 compliance center](https://compliance.microsoft.com/?azure-portal=true), select **eDiscovery** > **Core**.
2. Select a case.  ‎
3. On the **Core eDiscovery** page, select the **Searches** tab from the top pane. 
4. Select the dropdown arrow right from **+ New search** and select **+ Guided Search**.  ‎
5. On the **Name your search** page, enter a meaningful **Name** and a **Description**, that tells the purpose of this search on context of this eDiscovery case.  
6. Select **Next**.  
7. On the **Locations** page, select the following:

	- **Specific locations** to choose a location from the list below.  

	- **Locations on hold** to search only the data that is protected by a hold from the same case.
	
8. After choosing the desired locations, select **Next**.  
9. On the **Define your search condition** page, enter keywords for the search or select **+ Add conditions** to perform a more granular search. Any element found that contains these keywords is displayed in the result of the search.  
10. Select **Submit** to create the search within the eDiscovery case.

After the search is completed, you can preview the search results.

## Export content from a case

After a search associated with a Core eDiscovery case is successfully run, you can export the search results. 

Follow these steps to export the results of a content in an eDiscovery case:

1. From the [Microsoft 365 compliance center](https://compliance.microsoft.com/?azure-portal=true), select **eDiscovery** > **Core**.

2. On the **Core eDiscovery** page, select the name of the case that you want to create the hold in.

3. On the **Home** page for the case, select the **Searches** tab.

4. On the **Actions** menu at the bottom of the flyout page, select **Export results**.

   The workflow to export the results of a search associated with a Core eDiscovery case is that same as exporting the search results for a search on the **Content search** page.
  
5. Select the **Exports** tab in the case to display the list of export jobs.

   You may have to select **Refresh** to update the list of export jobs so that it shows the export job you created. Export jobs have the same name as the corresponding search with **_Export** appended to the search name.

6. Select the export job you created to display status information on the flyout page. This information includes the percentage of items that have been transferred to the Azure Storage location.

7. After all items have been transferred, select **Download results** to download the search results to your local computer. 


For additional information, see 

* [eDiscovery cases in the Microsoft 365 compliance center](/microsoft-365/compliance/ediscovery-cases)



 
