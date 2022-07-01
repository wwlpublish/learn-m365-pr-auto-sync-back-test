When an organization responds to a legal investigation, the workflow around identifying, preserving, and collecting potentially relevant content is based on the people in the organization who are the custodians of relevant data. In eDiscovery, these individuals are called **data custodians** (or just **custodians**). They're defined as "persons having administrative control of a document or electronic file". For example, the custodian of an email message could be the owner of the mailbox that contains the relevant message.

While there may be content located in mailboxes and sites that's not associated with a custodian, it may still be relevant to the case. Content locations where case custodians don't have administrative control but may be owners of relevant data are known as **non-custodial data sources**.

In an eDiscovery (Premium) case, legal teams can:

 -  Add individuals in their organization as custodians.
 -  Identify and preserve custodial data sources, such as Exchange mailboxes, OneDrive accounts, and SharePoint and Teams sites.
 -  Identify and preserve non-custodial data sources.

When an organization uses the built-in custodian and data source management tool in eDiscovery (Premium), it can secure electronically stored information from inadvertent (or intentional) deletion. Doing so eliminates the time-consuming and error-prone process of manually having to perform the legal hold processes.

### Add custodians to an eDiscovery (Premium) case

An organization can use the built-in custodian management tool in Microsoft Purview eDiscovery (Premium) to coordinate its workflows around managing custodians and identifying relevant, custodial data sources associated with a case. When a custodian is added to a case, the system can automatically identify and place a hold on their Exchange mailbox and OneDrive for Business account. During the investigation's discovery process, an organization can also identify other data sources (such as mailboxes, sites, or Teams) that a custodian accessed or contributed to. In this situation, the custodian management tool can be used to associate those data sources with a specific custodian. After custodians are added to a case and other data sources are associated with them, an organization can quickly preserve data and search the custodial data.

Custodians can be added to and managed in eDiscovery (Premium) cases in four steps, each of which is examined in greater detail in the following sections:

1.  Identify the custodians.
2.  Choose custodian data locations.
3.  Configure hold settings.
4.  Review the custodians and complete the process.

> [!NOTE]
> To add custodians to a case, you must be a member of the **eDiscovery Manager** role group. This role group provides the necessary permissions to add custodians to a case and place a hold on the custodial data sources.

### Step 1: Identify custodians

Perform the following steps to add custodians to an eDiscovery (Premium) case:

> [!NOTE]
> You must be assigned the **eDiscovery Manager** role group to have permissions to add custodians to a case.

1.  In the **Microsoft Purview compliance** portal, select **eDiscovery** in the navigation pane. In the expanded eDiscovery group, select **Premium**.
2.  On the **eDiscovery (Premium)** page, the **Overview** tab is displayed by default. Select the **Cases** tab that appears next to it.
3.  On the **Cases** tab, select the case that you want to add custodians to.
4.  On the detail page for the selected case, select the **Data sources** tab.
5.  On the **Data sources** tab, select **Add data source** on the menu bar. In the drop-down menu that appears, select **Add new custodians**.
6.  Add one or more users in your organization as custodians to the case by typing the first part of a person's name or alias. Both active and inactive users are searched. After you find the correct person, select their name to add them to the list. Select **Next** once you're finished adding custodians to the case.
7.  On the **Hold settings** page that appears, choose which of the new custodians to place on hold (all custodians are selected by default). Select **Next**.
8.  On the **Review your custodians** page, select **Submit.**
9.  On the **New custodians created** page, select **Done**.
10. On the **Data sources** tab, the selected custodians should now appear in the list of data sources.

### Step 2: Choose custodian data locations

After an organization selects custodians, the system automatically attempts to identify and verify these users and their data sources. It includes the primary mailbox and OneDrive account for each active user that has been added as a custodian. If the user is inactive, the tool only identifies the primary mailbox. An organization can choose not to include these data sources when adding custodians to the case.

In addition to a custodian's mailbox and OneDrive account, an organization can also associate other data locations to a custodian. For example, a SharePoint site or a Microsoft Team the custodian is a member of. This process enables an organization to preserve, collect, analyze, and review content in other data sources associated with the custodians of the case.

Perform the following steps to deselect the primary mailbox and OneDrive account for a custodian:

1.  Expand the custodian to view the primary data locations that have been automatically associated to each custodian.
2.  Select **Clear** next to **Mailbox** or **OneDrive** to remove a custodian's Exchange mailbox or OneDrive account from being associated as a data location for this custodian.
    
    :::image type="content" source="../media/configure-custodian-locations-af7e5008.png" alt-text="Screenshot of the Select custodian screen with the Clear option highlighted for the user's Exchange mailbox and OneDrive account.":::
    

Perform the following steps to associate other mailboxes, sites, Teams, or Yammer groups to a specific custodian:

1.  Expand a custodian to display the following services to associate data locations with the custodian. Select **Edit** next to a service to add one of the following data locations:
     -  **Exchange**. Associates other mailboxes to the custodian. Type into the search box the name or alias (a minimum of three characters) of user mailboxes or distribution groups. Select the mailboxes to assign to the custodian and then select **Add.**
     -  **SharePoint**. Associates SharePoint sites to the custodian. Select a site in the list or search for a site by typing a URL in the search box. Select the sites to assign to the custodian and then select **Add**. If a user is inactive, their OneDrive site must be added here as another SharePoint location.
     -  **Teams**. Assigns the Microsoft Teams in which the custodian is currently a member of. Select the teams to assign to the custodian and then select **Add**. After you add a team, the system automatically identifies and locates both the SharePoint site and the group mailbox associated with that team. It then assigns them to the custodian.
     -  **Yammer**. Assigns the Yammer groups the custodian is currently a member of. Select the groups to assign to the custodian and then select **Add**. After you add a team, the system automatically identifies and locates both the SharePoint site and the group mailbox associated with that group. It then assigns them to the custodian.
    
    > [!NOTE]
    > The Exchange and SharePoint location pickers can be used to associate any mailbox or site in an organization to a custodian. , This includes associating the mailbox and site for a Microsoft Team or Yammer group that a custodian isn't a member of. To do so, you must add both the mailbox and site associated with each team or Yammer group.
2.  You can view the total number of mailboxes, sites, Teams, and Yammer groups assigned to each custodian by expanding each custodian in the table. When you've finalized the assigned data locations for each custodian, these associations are maintained and used during the collection, processing, and review stages in the eDiscovery (Premium) workflow.
3.  After adding custodians and configuring their data locations, select **Next** to go to the **Hold settings** page.

### Step 3: Configure hold settings

After an organization has finalized the custodians and their data locations, it can place some or all of the custodians on hold. When a custodian is placed on hold, all content in all content locations that are associated with the custodian is preserved until you remove the hold or release the custodian from the hold. In some cases, you may want to add custodians to a case without placing them on hold.

Perform the following steps to place the custodians and data sources on hold:

1.  On the **Hold settings** page, you can apply a hold to individual custodians by selecting the check box under the **Hold** column. Alternatively, you can place all custodians on hold by selecting the **Hold** check box at the top of the column.
2.  Verify the custodian hold selections and then select **Next**.
    
    > [!NOTE]
    > If you don't place a hold on a custodian, the custodian and their associated data sources will be added to the case. However, the content in those data sources won't be preserved by the hold that's associated with the case.

### Step 4: Review the custodians and complete the process

Before you actually add the custodians to the case, you can review the list of custodians, the data locations assigned to them, and the hold settings. To review the custodians, perform the following steps:

1.  Verify and review all the data sources and the hold setting associated with each custodian in the table. If necessary, go back to the **Identify custodian** or **Hold settings** pages to make any changes.
2.  Select **Submit** to add custodians and their data locations to the case and apply all custodial hold settings. The new custodians are added to the case and displayed on the **Data sources** tab.
    
    :::image type="content" source="../media/data-sources-tab-1843ae4e.png" alt-text="Screenshot of the Data sources tab for a case that shows the custodians that were added to the case.":::
    
