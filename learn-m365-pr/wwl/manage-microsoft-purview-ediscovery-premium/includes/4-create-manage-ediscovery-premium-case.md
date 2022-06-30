After setting up Microsoft Purview eDiscovery (Premium) and assigning permissions to eDiscovery managers who will manage cases, the next step is to create and manage a case.

More organizations are using the eDiscovery (Premium) solution in Microsoft Purview for critical eDiscovery processes. This includes responding to regulatory requests, investigations, and litigation. As usage of eDiscovery (Premium) increases, a common customer requirement is to expand the total amount of content that can be managed in a single case. eDiscovery (Premium) cases are designed to help accommodate significant increases in case size, both for total data volume and the total number of items.

This unit provides a high-level overview of using cases to manage the eDiscovery (Premium) workflow for a legal case or other types of investigations.

### Create a case

Perform the following steps to create an eDiscovery (Premium) case:

1.  In the **Microsoft Purview compliance** portal, select **eDiscovery** in the navigation pane. In the expanded eDiscovery group, select **Premium**.
2.  On the **eDiscovery (Premium)** page, the **Overview** tab is displayed by default. Select the **Cases** tab that appears next to it.
3.  On the **Cases** tab, select **+Create a case** in the menu bar.
4.  On the **New eDiscovery case** pane that appears, enter a **Name** for the case. You can optionally enter a case **Number** and **Description**. The case name must be unique in the organization.
    
    :::image type="content" source="../media/new-ediscovery-case-form-71b70e2a.png" alt-text="Screenshot showing the New eDiscovery Case form.":::
    
5.  In the **Do you want to configure additional settings after creating this case?** option, select either:
     -  **Yes, I want to add members or configure the analytics section**.
     -  **No, retrun to the home page. I'll use the default case settings for**
6.  In the **Case format** section, select **New**. The Classic case option is being deprecated, so it's recommended that you select the **New case** format.
7.  Select **Save** to create the case.
8.  If you earlier selected the **Yes, I want to add members or configure the analytics** option, the case's detail page is returned, and the **Settings** tab is displayed.
9.  On the **Settings** tab, tiles appear for **Case information**, **Access and permissions**, and **Search and analytics**. Select the **Select** button for each tile that you want to update. The remaining steps describe how to update each tile.
    1.  If you select the **Select** button for the **Case information** tile, the **Case Information** pane will appear.
        1.  On the **Case Information** pane, you can modify the case number and descripion.
        2.  If you select the **Action** button at the bottom of the pane, a menu appears that enables you to close the case, delete the case, and copy support information.
        3.  When you've finished updating the case, select **Exit** to return to the **Settings** tab on the case's detail page.
    2.  If you select the **Select** button for the **Access and permissions** tile, the **Access and permissions** pane will appear.
        1.  On the **Access and permissions** pane, you can manage the members and role groups assigned to the case.
        2.  After adding and/or removing members and role groups, select **Exit** to return to the **Settings** tab on the case's detail page.
    3.  If you select the **Select** button for the **Search and analytics** tile, the **Search and analytics** pane will appear.
        1.  On the **Search and analytics** pane, you can modify various settings associated with this function.
        2.  Select **Save** to update your changes, and then select **Exit** to return to the **Settings** tab on the case's detail page.

### Benefits of the eDiscovery (Premium) case format

The eDiscovery (Premium) case format enables organizations to manage cases that contain over 40 million items. This capability helps companies to effectively manage large volumes of case data through the entire eDiscovery workflow. The eDiscovery (Premium) case format provides a list of other benefits for large cases in the eDiscovery (Premium) workflow, including:

 -  **Collection.** In the eDiscovery (Premium) case format, organizations can collect up to 1 TB of data for a single collection. For each case, the collection settings default to collect cloud attachments and contextual Teams and Yammer content. These settings help to collect the full picture of digital communications within an investigation. For Teams and Yammer contextual conversations, the eDiscovery (Premium) case format converts time-based snapshots of 1:1, 1: N and Channel conversations into HTML transcripts. Doing so provides context of conversations and reduces the total number of items produced by chat-based content.
    
        > [!WARNING]
        > If you attempt to collect over 1 TB in a single collection, the performance will be negatively impacted and may cause instability in some instances.
    
        > [!NOTE]
        > If cloud attachments are included by default in the large case format, an organization can remove that content from its review experience. It can do so by using review set filters to filter by message kind. Or, it can exclude cloud attachments by using the HasAttachment filter. For more information, see [Query and filter content in a review set](/microsoft-365/compliance/review-set-search?azure-portal=true).
 -  **Review**. Each review set will support up to 1 TB of pre-expansion content. Additional metadata is available for filters and queries including Team name, channel name, and conversation name for Teams content. Each transcript includes time-based content for before and after the responsive item. For Channel conversations, the root post and all replies are collected for responsive content. For more information, see [eDiscovery (Premium) workflow for content in Microsoft Teams (preview)](/microsoft-365/compliance/teams-workflow-in-advanced-ediscovery?azure-portal=true)
 -  **Export**. An organization can export large sets of content in a single export job. The eDiscovery (Premium) case format can export 5 million documents or 500 GB, whichever is smaller in an export job.
    
        > [!NOTE]
        > When exporting chat conversation transcripts, all metadata for a conversation is embedded in the HTML transcript file. Many of the common fields are available in the load file. For more information about exported metadata, see [Document metadata fields in eDiscovery (Premium)](/microsoft-365/compliance/document-metadata-fields-in-advanced-ediscovery?azure-portal=true).

The user interface for the eDiscovery (Premium) case format displays the total size of each review set in the case. Review set sizes are displayed in a column on the **Review sets** tab.

:::image type="content" source="../media/largecaseui-ac0858fd.png" alt-text="Screenshot showing the Review sets tab on the case detail page where the size of each review set is highlighted.":::
