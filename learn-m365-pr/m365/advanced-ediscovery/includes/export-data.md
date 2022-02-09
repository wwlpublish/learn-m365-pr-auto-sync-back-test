After you have finished culling your data in a review set to the content that is most relevant, you can download or export content for presentation or external review. This is the *Export data* phase of the EDRM workflow.

> [!div class = "centered"]
> :::image type="content" source="../media/edrm-model-5.png" alt-text="Seventh phase of the EDRM model – Export data." lightbox="../media/edrm-model-5.png":::

### Download documents from a review set

In some cases, you may just need to download a few documents from a case for a specific deposition. The **Download** option is the quickest way to export a small set of data while preserving the native file names. It leverages a browser's data transfer features so a browser prompt will appear once a download is ready. Files downloaded using this method will be zipped into a container file and will be item level files. This means that if you select an attachment, you will automatically receive the email with the attachment included. Similarly, if you select an Excel spreadsheet that was embedded in a word document, you will receive the word document with the Excel spreadsheet embedded. Downloaded items will preserve the last modified date which can be viewed as a file property.

To download content from a review set, start by selecting the files you want to download then click **Download** under the **Action** menu.

:::image type="content" source="../media/download.png" alt-text="Download content screen from a review set." lightbox="../media/download.png" border="false":::

### Export documents from a review set

For bigger volumes, you can use the **Export** option. Export lets you customize the content that is included in the download package. This includes exporting file metadata, native files, text files, and redacted documents that have been saved to a PDF file. After the exported data is uploaded to an Azure Storage location, you can download it to a local computer.

To export content from a review set, start by selecting the files you want to download then click **Export** under the **Action** menu.

 :::image type="content" source="../media/export.png" alt-text="Export content screen from a review set." lightbox="../media/export.png" border="false":::

## Download export jobs using Azure Storage Explorer

When you export documents from a review set in an Advanced eDiscovery case, you have the ability to either upload the documents to a Microsoft-provided Azure Storage location, or to an Azure Storage location managed by your organization.

A configuration page provides you with the following options for how to export the content, enabling you to choose the settings that make the most sense in the context of your investigation:

- **Metadata file**. This can be considered your "load file" that contains metadata associated with the files you export. For a list of exported fields available in the metadata file, see [Document metadata fields in Advanced eDiscovery](/microsoft-365/compliance/document-metadata-fields-in-advanced-ediscovery?azure-portal=true). This file can typically be ingested by third-party tools.
- **Tag data**. This content would be added as fields in the metadata file. It contains all the tag information applied in review sets.
- **Text files**. Text files can be generated for each file exported from a review set. Often, these files are required by service partners as part of ingesting data into third-party tools.
- **Redacted files**. If redacted PDF files are generated during review, these files are available during export. You can decide whether to export native files only or to replace the native files that required redaction with the PDF files that contain the actual redactions.
- **Export location**. Exported content is delivered to either a Microsoft provided Azure Storage location or a customer's storage location.

Before you can export content, you need to install the [Azure Storage Explorer tool](https://go.microsoft.com/fwlink/p/?LinkId=544842?azure-portal=true). Azure Storage Explorer is used to connect to the Azure storage container to browse and download the exported documents.

To export content:

1. Select the files you want to export from the review set, then click **Export** under the **Action** menu. It may take several minutes or longer before the content is ready. You can check the status on the **Jobs** page.
1. Select your settings on the **Export options** configuration page, then click **Export**. In this example, the Microsoft-provided storage container is selected.

    :::image type="content" source="../media/export-options.png" alt-text="Export content, step 1." lightbox="../media/export-options.png":::

    A message appears to inform you that a job has been created and that you can track its status on the **Jobs** tab.

    :::image type="content" source="../media/ok.png" alt-text="Export content, step 2.":::

1. When the documents have been successfully uploaded to the Azure storage container, the **Jobs** tab will display the Status of the job as Successful along with the time stamp for when the job completed.

    :::image type="content" source="../media/status.png" alt-text="Export content, step 3." lightbox="../media/status.png" border="false":::

1. The next step is to obtain the shared access signature (SAS) URI that is generated when you created the export job. On the **Exports** tab, click the export job that you want to download. On the flyout page, under **Locations**, copy the SAS URI that is displayed to the clipboard, then click **Close**.

    :::image type="content" source="../media/sas-url.png" alt-text="Export content, step 4." lightbox="../media/sas-url.png" border="false":::

1. Open the Azure Storage Explorer tool that you installed in Step 1, then select **Use a shared access signature (SAS) URI**. Click **Next**.

    :::image type="content" source="../media/connect-azure-storage.png" alt-text="Export content, step 5." border="false":::

1. On the **Attach with SAS URI** page, click in the URI box, and then paste the SAS URI that you copied in Step 4. Notice that a portion of the SAS URI is displayed in the **Display name** box. This will be used as the display name of the container that is created under the **Storage accounts** after you connect to the storage location. This name consists of the ID of the Advanced eDiscovery case is from and a unique identifier. You can keep the default display name or change it. If you change it, the display name must be unique.

    :::image type="content" source="../media/attach-sas-url.png" alt-text="Export content, step 6." border="false":::

1. Click **Next** to display the **Connection summary** page.

    :::image type="content" source="../media/connect-summary.png" alt-text="Export content, step 7." lightbox="../media/connect-summary.png" border="false":::

1. On the **Connection summary** page, review the connection information, then click **Connect**.

    The **Blob containers** node (under **Storage Accounts > Attached Containers**) is opened to a container with the display name from step 7. This container contains a folder for each export job that you have created. The folders are named with an ID that corresponds to the ID of the export job.

    :::image type="content" source="../media/containers-1.png" alt-text="Export content, step 8." lightbox="../media/containers-1.png":::

1. Double-click the export job folder to open it and display the list of folders and export reports.

    :::image type="content" source="../media/containers-2.png" alt-text="Export content, step 9." lightbox="../media/containers-2.png" border="false":::

1. To export all contents in the export, select the export folder, and then click **Download**.

    > [!NOTE]
    > Instead of downloading the entire export job, you can select specific items to download. And instead of downloading items, you can double-click an item to view it.

1. Specify the location where you want to download the exported files, and then click **Select folder**. The Azure Storage Explorer starts the export process and a message is displayed when the download is finished.

### Export structure

When content is exported from a review set, the content is organized in the following structure.

Root folder – Download ID

- Extracted_text_files = contains all of the extracted text files generated at processing.
- Input_or native_files = contains all native files
- Export_load_file.csv = metadata file
- Summary.txt = a summary file with export statistics
- Error_files = contains any error files included in the export
  - ExtractionError – a csv that contains any available metadata of files that were not properly extracted from parent files
  - ProcessingError – content with processing errors. This content is item level meaning if an attachment experienced a processing error, the email that contains the attachment will be included in this folder.

## Learn more

- [Document metadata fields in Advanced eDiscovery](/microsoft-365/compliance/document-metadata-fields-in-advanced-ediscovery?azure-portal=true)
- [Azure Storage Explorer tool](https://go.microsoft.com/fwlink/p/?LinkId=544842?azure-portal=true)
