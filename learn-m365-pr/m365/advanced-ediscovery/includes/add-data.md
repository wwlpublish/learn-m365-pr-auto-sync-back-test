This section discusses the *Review*, or Early Case Assessment (ECA), phase of the EDRM model.

> [!div class = "centered"]
> :::image type="content" source="../media/edrm-model-3.png" alt-text="Fifth phase of the EDRM model – Review." lightbox="../media/edrm-model-3.png":::

After you've collected all data relevant to the case, the next step is process it for further review. In Advanced eDiscovery, the live, in-place data that you identified in the collection phase is copied offline to an Azure Storage location called a review set.

Review sets are a static set of documents where you can analyze, query, view, tag, and export data in a case. Copying the data to the review set enhances the review and analysis process by providing you with advanced analytics such as themes detection, near-duplicate detection, and email thread identification.

There are various methods for adding data to a review set in an Advanced eDiscovery case, including:

- Adding search results to a review set.
- Adding non-Office 365 data to a review set.
- Adding data from a review set to another review set.

:::image type="content" source="../media/add-data.png" alt-text="Three methods for adding data to a review set in an Advanced eDiscovery case.":::

## Add search results to a review set

After you are satisfied with the collection of custodial content, you can evaluate the content further by moving it into a review set in the case. You do this by selecting a search on the **Searches** tab, and then clicking **Add results to review set** on the flyout page.

 :::image type="content" source="../media/add-results.png" alt-text="Evaluate the collection of custodial content further by moving it into a review set in the case." lightbox="../media/add-results.png":::

Adding the results of your search to a review set triggers Advanced eDiscovery to collect all the content from your search results. It then processes all that content by extracting the text and metadata and places the results in a centralized index. These results from the sources you selected can then be searched and analyzed through one interface.

> [!NOTE]
> Adding data to a review set is a long-running process. This process includes gathering items from the original data sources in Microsoft 365 (for example, from mailboxes and sites), copying them to the Azure Storage location, and then re-indexing the items. You can track the progress on the Jobs tab or on the Searches tab by monitoring the status in the Added data to review set column.

After the review set processing is completed, you can click the Review sets tab in the case, and click the review set to start the process of filtering, reviewing, tagging, and exporting data in the review set.

## Load non-Microsoft 365 data into a review set

Not all content that you need to analyze in Advanced eDiscovery is in Microsoft 365. If you want to add data from a source other than Office 365 into your search – including data from an on-premises environment - a process is provided to add that data after you complete your initial search. With the non-Microsoft 365 data import feature in Advanced eDiscovery, you can upload documents that aren't located in Microsoft 365 to a review set. 

> [!NOTE]
> Non-Microsoft 365 data must be a file type that is supported by Advanced eDiscovery. For more information, see [Supported file types in Advanced eDiscovery](/microsoft-365/compliance/supported-filetypes-ediscovery20?azure-portal=true).

### Before you begin

Loading non-Microsoft 365 data into a review set leverages an Azure AzCopy command that contains parameters with the location of where the files that you want to upload are stored and the Azure storage location that the files will be uploaded to. Therefore, before you attempt to load non-Microsoft 365 data, it is necessary to [install the AzCopy command-line utility](/azure/storage/common/storage-use-azcopy-v10?azure-portal=true) to your local computer in the default location, which is **%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy**.  

The files to be uploaded must be located in subfolders, where each subfolder is associated with a specific custodian using the following naming convention: **alias\@domainname**. The alias@domainname must be the user's Microsoft 365 alias and domain. The parent folder can only contain the alias@domainname folders without any loose files. As an example, the folder structure for the non-Microsoft 365 data that you want to upload would be similar to the following:

- c:\nonO365\abraham.mcmahon@contoso.com
- c:\nonO365\jewell.gordon@contoso.com
- c:\nonO365\staci.gonzalez@contoso.com

:::image type="content" source="../media/file-structure.png" alt-text="Required file structure":::

## Upload non-Microsoft 365 data

1. In Advanced eDiscovery, navigate to the **Review sets** tab, then select the review set to upload the non-Microsoft 365 data to.
1. In the review set, click **Manage review set**, and then click **View uploads** on the **Non-Microsoft 365 data** tile.
1. Click **Upload files** to start the data import wizard.

    :::image type="content" source="../media/review-set.png" alt-text="Click Upload files to start the data import wizard.":::

    The first step in the wizard prepares a secure Microsoft-provided Azure Storage location to upload the files to. When the preparation is completed, the **Next: Upload files** button becomes active.

    :::image type="content" source="../media/non-office-data.png" alt-text="The first step in the wizard prepares a secure Microsoft-provided Azure Storage location to upload the files to. When the preparation is completed, the Next: Upload files button becomes active.":::

1. Click **Next: Upload files**.
1. On the **Upload files** page, verify or type the location of the root folder where you've stored the non-Microsoft 365 data you want to upload in the **Path to location of files** box. Next, click **Copy to clipboard** to copy the command that is displayed in the box.

    :::image type="content" source="../media/non-office-data-upload-files.png" alt-text="Upload files screen":::

1. Open a Windows command prompt (Run as administrator), paste the command that you copied in the previous step, and then press **Enter** to start the AzCopy command. After you start the command, the non-Microsoft 365 files will be uploaded to the Azure Storage location that was prepared in step 3.

    :::image type="content" source="../media/process-files-2.png" alt-text="Command prompt commands" lightbox="../media/process-files-2.png":::

1. Return to the data import wizard in Advanced eDiscovery and click **Next: Process files**. This initiates processing, text extraction, and indexing of the non-Microsoft 365 files that were uploaded to the Azure Storage location.
1. After the processing is finished, you can close the wizard.

    > [!NOTE]
    > You can track the progress of processing the files on the **Process files** page or on the **Jobs** tab by viewing a job named **Adding non-Microsoft 365 data to a review set**.

## Add data to a review set from another review set

In some cases, it may be necessary to select content from one review set and work with them individually in another review set. This is especially useful if you've culled content in a review set and want to run analytics on the subset of data.

Before you start, you will need to create a new review set to add the data to. A new review set can be added on the **Review sets** tab of the case by clicking **Add Review Set**.

:::image type="content" source="../media/add-review-set.png" alt-text="Create a new review set to add the data to." lightbox="../media/add-review-set.png":::

You can add content from one review set to another one by selecting specific documents in the source review set or by selecting all items returned by review set query. If you are adding selected items, select the items, select **Action**, and then select **Add to another review set**.

:::image type="content" source="../media/action.png" alt-text="Adding selected items." lightbox="../media/action.png":::

In the **Add to another review set** flyout page, choose the review set you want to add the items to. Choose whether to add **All documents in the review set** or **Selected documents only**. **Additional information** provides options to include metadata from the items and whether to include [tags](/microsoft-365/compliance/tagging-documents?azure-portal=true) from the source review set when the documents are added to the new review set.

 :::image type="content" source="../media/add-to-another-review-set.png" alt-text="Add to another review set options flyout page":::

### What is a load set?

Investigations may be conducted over the course of weeks or even months. As the case progresses, you may discover that there may be additional data sources relevant to a specific custodian. This may require you to create multiple searches over the course of time so that your review set includes all the data that is relevant to the case.

A load set is an instance of adding data to a review set. For example, if you add the results of two different searches to the same review set, each will represent a load set.
