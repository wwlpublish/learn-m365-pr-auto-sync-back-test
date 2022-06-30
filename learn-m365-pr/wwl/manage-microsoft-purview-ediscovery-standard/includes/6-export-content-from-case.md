After an organization successfully runs a search associated with a Microsoft Purview eDiscovery (Standard) case, the company can export the search results.

 -  When search results are exported, mailbox items are downloaded in PST files or as individual messages.
 -  When content from SharePoint and OneDrive for Business sites are exported, copies of native Office documents and other documents are exported.
 -  The following files are also exported:
     -  A **Results.csv** file that contains information about every item that's exported.
     -  A manifest file (in XML format) that contains information about every search result.

### Export search results

Organizations should complete the following steps to export the search results for an eDiscovery (Standard) case:

1.  In the **Microsoft Purview compliance** portal, select **eDiscovery** in the navigation pane to expand the group. Under the **eDiscovery** group, select **Standard**.
2.  On the **eDiscovery (Standard)** page, select the name of the case that you want to create the hold in.
3.  On the case's detail page, select the **Searches** tab.
4.  On the **Actions** menu at the bottom of the detail pane, select **Export results**.
    
    :::image type="content" source="../media/actionmenuexportresults-cf530593.png" alt-text="Screenshot showing the Action menu with the Export results option highlighted.":::
    
    
    The workflow to export the results of a search associated with a eDiscovery (Standard) case is the same as exporting the search results for a search on the **Content search** page. For step-by-step instructions, see the training module titled: **Search for content in the Microsoft Purview compliance portal**.
    
    > [!NOTE]
    > When an organization exports search results, it can enable de-duplication so that only one copy of an email message is exported. It can do so even though multiple instances of the same message may have been found in the mailboxes that were searched. For more information about de-duplication and how duplicate items are identified, see [De-duplication in eDiscovery search results](/microsoft-365/compliance/de-duplication-in-ediscovery-search-results?azure-portal=true).
    
    After the export is started, the search results are prepared for downloading. As a result, they're transferred to a Microsoft-provided Azure Storage location in the Microsoft cloud.
5.  On the case's detail page, select the **Exports** tab to display the list of export jobs related to that case.
    
    :::image type="content" source="../media/coreediscoveryexport-64b15119.png" alt-text="Screenshot of a case's detail page showing the Exports tab and two export jobs that were run for the case.":::
    
    
    > [!NOTE]
    > The export job you created may not appear in the list of exports. If this situation occurs, select **Refresh** on the menu bar to update the list of export jobs. Export jobs have the same name as the corresponding search. However, they also have **\_Export** appended to the search name.
6.  Select the export job you created to display status information on the job's detail pane. This information includes the percentage of items that have been transferred to the Azure Storage location.
7.  After all items have been transferred, select **Download results** to download the search results to your local computer.

> [!IMPORTANT]
> The exported search results must be downloaded within 14 days after the export job was created.

**Additional reading**. For more information about the export files that are included when you export search results, see [Export a Content search report](/microsoft-365/compliance/export-a-content-search-report?azure-portal=true).

### Restart an export job

If you restart an export job, any changes to the queries of the searches that make up the export job won't affect the search results that are retrieved. When you restart an export, the same combined search query job that was run when the export job was created will be run again.

Also, if you restart an export, the search results that are copied to the Azure Storage location overwrite the previous results. The previous results that were copied won't be available to be downloaded.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”