Once organizations run a search and view the search results and statistics, they may optionally decide to export the search results and search report. This unit examines each of these tasks.

### Export the search results

After a Content search is successfully run, the search results can be exported to a local computer. When you export email results, they're downloaded to your computer as PST files. When you export content from SharePoint and OneDrive for Business sites, copies of native Office documents are exported. There are other documents and reports included with the exported search results.

Exporting the results of a Content search involves preparing the results, and then downloading them to a local computer.

#### Step 1: Prepare search results for export

The first step is to prepare the search results for exporting. When you prepare results, they're uploaded to a Microsoft-provided Azure Storage location in the Microsoft cloud. Content from mailboxes and sites is uploaded at a maximum rate of 2 GB per hour.

1.  In the Microsoft 365 compliance center, select the content search that you want to export results from.
2.  On the **Actions** menu at the bottom of the flyout page, select **Export results**. The **Export results** flyout page is displayed.
3.  On the **Export results** flyout page, the export options that are displayed depend on whether search results are located in mailboxes or sites or a combination of both. Under **Output options**, choose one of the following options:
    
    :::image type="content" source="../media/export-output-options-8d94b2f6.png" alt-text="screenshot showing the options for exporting the search results":::
    
    
     -  **All items, excluding ones that have unrecognized format, are encrypted, or weren't indexed for other reasons.** This option exports only indexed items.
     -  **All items, including ones that have unrecognized format, are encrypted, or weren't indexed for other reasons.** This option exports indexed and unindexed items.
     -  **Only items that have an unrecognized format, are encrypted, or weren't indexed for other reasons.** This option exports only unindexed items.
4.  Under **Export Exchange content as**, choose one of the following options:
    
    :::image type="content" source="../media/exchange-export-options-88d887af.png" alt-text="screenshot showing the options for exporting the Exchange content that are described below this image":::
    
    
     -  **One PST file for each mailbox.** Exports one PST file for each user mailbox that contains search results. Any results from the user's archive mailbox are included in the same PST file. This option reproduces the mailbox folder structure from the source mailbox.
     -  **One PST file containing all messages.** Exports a single PST file (named *Exchange.pst*) that contains the search results from all source mailboxes included in the search. This option reproduces the mailbox folder structure for each message.
     -  **One PST file containing all messages in a single folder.** Exports search results to a single PST file where all messages are located in a single, top-level folder. This option lets reviewers review items in chronological order (items are sorted by sent date) without having to navigate the original mailbox folder structure for each item.
     -  **Individual messages.** Exports search results as individual email messages, using the .msg format. If you select this option, email search results are exported to a folder in the file system. The folder path for individual messages is the same as the one used if you exported the results to a PST file.
5.  Configure the remaining options:
    
    :::image type="content" source="../media/other-export-options-3d93d52c.png" alt-text="screenshot showing the remaining export options that are described below this image":::
    

    **A. Enable de-duplication for Exchange content.** Select this checkbox to exclude duplicate messages. If you select this option, only one copy of a message will be exported even if multiple copies of the same message are found in the mailboxes that were searched. The export results report (which is a file named Results.csv) will contain a row for every copy of a duplicate message so that you can identify the mailboxes (or public folders) that contain a copy of the duplicate message. For more information about de-duplication and how duplicate items are identified, see [De-duplication in eDiscovery search results](/microsoft-365/compliance/de-duplication-in-ediscovery-search-results).

    **B. Include versions for SharePoint files.** Select this checkbox to export all versions of SharePoint documents. This option appears only if the content sources of the search include SharePoint or OneDrive for Business sites.

    **C. Export files in a compressed (zipped) folder. Includes only individual messages and SharePoint documents checkbox to export search results to compressed folders.** This option appears only when you choose to export Exchange items as individual messages and when the search results include SharePoint or OneDrive documents. This option is primarily used to work around the 260 character limit in Windows file path names when items are exported.

6.  Select **Export** to start the export process. The search results are prepared for downloading, which means they're collected from the original content locations and then uploaded to an Azure Storage location in the Microsoft cloud. The export process may take several minutes to complete.

See the next section for instructions to download the exported search results.

#### Step 2: Download the search results<br>

The next step is to download the search results from the Azure Storage location to your local computer.

1.  On the **Content search** page in the Microsoft 365 compliance center, select the **Exports** tab.
    
    You may have to select **Refresh** to update the list of export jobs so that it shows the export job you created. Export jobs have the same name as the corresponding search with **\_Export** appended to the search name.
2.  Select the export job that you created in **Step 1-Prepare search results for export**.
3.  On the flyout page under **Export key**, select **Copy to clipboard**. This key will be used in step 6 to download the search results.

    > [!WARNING]
    > Because anyone can install and start the eDiscovery Export tool, and then use this key to download the search results, be sure to take precautions to protect this key just like you would protect passwords or other security-related information.

4.  At the top of the flyout page, select **Download results**.
5.  If you're prompted to install the **eDiscovery Export Tool**, select **Install**.
6.  In the **eDiscovery Export Tool**, complete the following steps:
    
     -  Paste the export key that you copied in step 3 in the appropriate box.
     -  Select **Browse** to specify the location where you want to download the search result files.

    :::image type="content" source="../media/ediscovery-export-tool-4851035a.png" alt-text="screenshot showing the eDiscovery export tool window and the field for pasting in the export key":::


    > [!CAUTION]
    > Because of high network activity during download, you should download search results only to a location on an internal drive on your local computer. For the best download experience, follow these guidelines:<br><br>\- Don't download search results to a UNC path, a mapped network drive, an external USB drive, or a synched OneDrive for Business account.<br>\- Disable anti-virus scanning for the folder that you download the search result to.<br>\- Download search results to different folders for concurrent download jobs.

7.  Select **Start** to download the search results to your computer.
    
    The eDiscovery Export Tool displays status information about the export process, including an estimate of the number (and size) of the remaining items to be downloaded. When the export process is complete, you can access the files in the location where they were downloaded.

### Export a Content search report

Instead of exporting the full set of search results from a Content search in the Microsoft 365 compliance Center, you can export the same reports that are generated when you export the actual search results.<br>

When you export a report, the report files are downloaded to a folder on your local computer that has the same name as the Content Search, but that's appended with *\_ReportsOnly*. For example, if the Content Search is named *ContosoCase0815*, then the report is downloaded to a folder named *ContosoCase0815\_ReportsOnly*. For a list of documents that are included in the report, see [What's included in the report](/microsoft-365/compliance/export-a-content-search-report).

#### Step 1: Generate the report for export

The first step is to prepare the report for downloading to your computer exporting. When you export the report, the report documents are uploaded to an Azure Storage area in the Microsoft cloud. The steps included in this task are similar to Step 1 in the **Export the search results** section above.

1.  In the Microsoft 365 compliance center, select the Content search that you want to export the report from.<br>
2.  On the **Actions** menu at the bottom of the search flyout page, select **Export report**. The **Export report** flyout page is displayed.<br>
3.  On the **Export report** flyout page, the export report options that are displayed depend on whether search results are located in mailboxes or sites or a combination of both. Under **Output options**, choose one of the available options. These options are similar to the ones that were displayed in Step 1 above when exporting search results. If necessary, see that step for an explanation of each option.<br>
4.  Configure the **Enable de-duplication for Exchange** content option.
    
     -  If you select this option, the count of duplicate messages (before de-duplication and after de-duplication) is included in the export summary report. Also, only one copy of a message will be included in the manifest.xml file. But the export results report will contain a row for every copy of a duplicate message so that you can identify the mailboxes that contain a copy of the duplicate message.
     -  If you don't select this option, the export reports will contain information about all messages returned by the search, including duplicates. For more information about de-duplication and how duplicate items are identified, see [De-duplication in eDiscovery search results](/microsoft-365/compliance/de-duplication-in-ediscovery-search-results).
5.  Select **Generate report**. The search reports are prepared for downloading, which means the report documents are uploaded to an Azure Storage location in the Microsoft cloud. It may take several minutes for the report to be generated.

See the next section for instructions to download the exported search reports.

#### Step 2: Download the report

The next step is to download the report from the Azure Storage area to your local computer. The steps in this task are similar to Step 2 in the **Export the search results** section above. Since you generated a report in the prior step, when you select the export job that you created in Step 1, the **Export report** flyout page will appear rather than the **Export results** page. However, all the steps on this page are similar to the **Export results** flyout page from the prior section when you downloaded the export results.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”