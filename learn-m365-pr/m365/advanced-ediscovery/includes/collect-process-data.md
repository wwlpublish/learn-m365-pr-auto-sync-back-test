
In this section, we discuss the *Collection* and *Processing* phases of the EDRM model.

> [!div class="centered"]
> :::image type="content" source="../media/edrm-model-2.png" alt-text="Third and fourth phases of the EDRM model – Collection and Processing.":::

After creating the case, adding the custodians and their associated data sources, the next step typically involves searching for and collecting relevant content to build out the case. You can quickly do this by creating a search.  

The process of creating a search begins from the **Searches** tab in your case, where you can create a new search by clicking **New search** and then completing the following steps:

1. Enter a name and description (optional).

    :::image type="content" source="../media/name-description.png" alt-text="Name and description fields.":::

1. Add the custodians relevant to the search.

    :::image type="content" source="../media/custodians.png" alt-text="Custodian field.":::

1. Select the locations to search, including any additional locations that weren't exposed during the hold process.

    :::image type="content" source="../media/locations.png" alt-text="Locations field." lightbox="../media/locations.png":::

1. Enter keywords and/or add conditions to narrow search results.

    :::image type="content" source="../media/search-criteria.png" alt-text="Keywords and conditions fields." lightbox="../media/search-criteria.png" border="false":::

## Build search queries and add conditions

When building search queries, you can use keywords to find specific content and conditions to narrow the scope of the search to return items that are most relevant to your investigation.

### Keyword searches

Using keywords enable you to get statistics that show how many items match each keyword in the keyword list. This can help you quickly identify the keywords that are the most or least effective. You can also use a keyword phrase, surrounded by parentheses, in a row in the keywords list.

The **Keywords** box supports keywords, email message properties (such as sent and received dates), document properties (such as file names or the date that a document was last changed), and queries that use a Boolean operator such as **AND, OR, NOT**, and **NEAR**. You can also search for sensitive information (such as Social Security numbers) in documents in SharePoint and OneDrive (not in email messages), or search for documents that have been shared externally. If you leave the **Keywords** box empty, all content located in the specified content locations is in the search results.

> [!NOTE]
> To optimize performance, you are limited to a maximum of 20 rows in the keyword list.

### Conditions

Conditions are granular parameters such as dates, authors, or email recipients that can be used to narrow the scope of a search and return a more refined set of results. Each condition adds a clause to the search query that is created and run when you start the search. A condition is logically connected to the keyword query specified in the keyword box by a logical operator (which is represented as c:c in the search query syntax) that is similar in functionality to the **AND** operator. That means that items must satisfy both the keyword query and one or more conditions to be included in the search results. This is how conditions help to narrow your results. For a list and description of conditions that you can use in a search query, see [Search conditions](/microsoft-365/compliance/keyword-queries-and-search-conditions?azure-portal=true).

## Validate search results

After executing a search, you can use **Statistics** and **Preview** options to verify the search you created is collecting the type of data you need.

:::image type="content" source="../media/search-custodian-data.png" alt-text="Statistics and Preview options verify the search." lightbox="../media/search-custodian-data.png" border="false":::

Statistics on the retrieved items lets you validate your search results and make sure they align with your expectations. You can see things such as the locations that had the most items that matched the search query, and the number of and size of unindexed items. To learn more about statistics, see [Search statistics](/microsoft-365/compliance/search-statistics?azure-portal=true).

:::image type="content" source="../media/search-statistics.png" alt-text="Statistics on the retrieved items lets you validate your search results and make sure they align with your expectations." lightbox="../media/search-statistics.png":::

Preview generates a sampling of the various data sources and provides another view for early validation that you are on the right track.

:::image type="content" source="../media/search-results.png" alt-text="Preview generates a sampling of the various data sources." lightbox="../media/search-results.png":::

You can also generate your own sample from a search.

:::image type="content" source="../media/sample.png" alt-text="You can also generate your own sample from a search." border="false":::

Generating a sample lets you use parameters such as confidence level and confidence interval.

:::image type="content" source="../media/sampling-parameters.png" alt-text="Generating a sample lets you use parameters such as confidence level and confidence interval.":::

## Content indexing of data

The next phase of the EDRM model, *Processing*, involves deep indexing of content including file identification, expansion of embedded documents and attachments, text extraction, and OCR (Optical Character Recognition) of image files.

The underlying content indexing engine is provided by Microsoft Search. This platform includes various components for crawling and indexing data, querying data, and searching data. eDiscovery relies on the Search system to crawl content and build an index that eDiscovery cases run queries against. As the Search system crawls content, it creates a search index. The search index stores data that is used to provide the results for search queries, including information about the permissions that are required to access each piece of content. When a user performs a search, the search system uses the search index to identify the appropriate search results. Before displaying the results, the search system performs *security trimming*. Security trimming is the process by which the system compares the user's permissions to the permissions that are required to access content that search results link to, and then "trims" the results to show only those results that the user has permission to view.

The search system is tuned for performance so you can search for content quickly. Because it's tuned for speed, there are mechanisms in place to identify and skip items that may take too long to process. Therefore, items such as large files or emails with several attachments may be skipped and remain unindexed so that search results can be returned more quickly. Content may also be partially indexed for reasons including encryption or password protection, the existence of images, unsupported file types or when indexing file size limits are encountered.

Advanced indexing is the process that reprocesses unindexed and partially indexed content to make it fully searchable.

The **Processing** tab in Advanced eDiscovery provides insight into the status of advanced indexing for different processing scenarios. In the **Index status** view on the **Processing** tab for a case, the graph lists the number of items added to the *hybrid index*. The hybrid index is where Advanced eDiscovery stores the reprocessed content.

:::image type="content" source="../media/processing.png" alt-text="The Processing tab in Advanced eDiscovery provides insight into the status of advanced indexing for different processing scenarios." lightbox="../media/processing.png":::

## Error remediation

Error remediation enables you to address issues that prevent Advanced eDiscovery from processing content. For example, files that are password protected cannot be processed since the files are locked or encrypted. Using error remediation, you can download files with such errors, remove the password protection, and then upload the remediated files.

Error remediation of documents leverages an Azure AzCopy command that contains parameters with the location of where the files that you want to upload are stored and the Azure storage location that the files will be uploaded to. Therefore, before you begin the process of error remediation, it is necessary to [install the AzCopy command-line utility](/azure/storage/common/storage-use-azcopy-v10?azure-portal=true) to your local computer in the default location, which is `%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy`.  

1. To begin the process of error remediation, select **Errors** in the **View** drop-down menu on the **Processing** tab and then select a case or review set from the **Scope** drop-down menu. This section displays all errors from the case or error from a specific review set. In the example below, an error was found in the Investigation – 01234 case.

    :::image type="content" source="../media/new-error-remediation.png" alt-text="Error remediation screen." lightbox="../media/new-error-remediation.png":::

1. To remediate the password protected file, select the radio button next to the file type, then click **New error remediation**. The error remediation process begins with a preparation stage where the files with errors are copied to a Microsoft-provided Azure Storage location so that you can download them to your local computer to remediate.

1. After the preparation is complete, click **Next: Download files** to proceed with the download.

    :::image type="content" source="../media/new-remediation.png" alt-text="Click Next: Download files to download." lightbox="../media/new-remediation.png":::

1. To download files, specify the **Destination path for download**. This is a path to the parent folder on your local computer where the file will be downloaded. The default path, %USERPROFILE%\Downloads\errors, points to the local user's download folder and can be changed if desired. For performance reasons, it is recommended that you do not use a remote network path.

    The path to the parent folder is automatically added to the AzCopy command as the value of the **/Dest** parameter.

1. Copy the predefined command by clicking **Copy to clipboard**, then open a Windows command prompt (Run as administrator), paste the AzCopy command, and then press **Enter**.

    :::image type="content" source="../media/command-prompt.png" alt-text="Paste the AzCopy command into the Windows command prompt and then press Enter." lightbox="../media/command-prompt.png":::

    The files that you selected are downloaded to the location that you specified in step 5. In the parent folder (for example, **C:\Remediation**), the following subfolder structure is automatically created:

    \<Parent folder>\Subfolder 1\Subfolder 2\\\<file>
     - *Subfolder 1* is named with the ID for the case or the review set, depending on the scope that you selected in step 1.
     - *Subfolder 2* is named with the file ID of the downloaded file
     - The downloaded file is located in *Subfolder 2* and is also named with the file ID.

    If multiple files are downloaded, each one is downloaded to a subfolder that is named with the file ID.

1. Return to the error remediation wizard in Advanced eDiscovery, then click **Next: Upload files**. This moves to the next page where you can now upload the files.

    :::image type="content" source="../media/download-files.png" alt-text="Download files screen." lightbox="../media/download-files.png":::

1. Specify the parent folder where the remediated files are located in the **Path to location of files** text box. The parent folder must have the same subfolder structure that was created when you downloaded the files. The path to the parent folder is automatically added to the AzCopy command as the value of the **/Source** parameter.

    :::image type="content" source="../media/upload-files.png" alt-text="Upload files screen." lightbox="../media/upload-files.png":::

1. Copy the predefined command by clicking **Copy to clipboard**. Open a Windows command prompt (Run as administrator), paste the AzCopy command, and then press **Enter** to upload the files.

    :::image type="content" source="../media/process-files.png" alt-text="Command prompt with AzCopy command." lightbox="../media/process-files.png":::

1. After you run the AzCopy command, click Next: **Process files**.

    :::image type="content" source="../media/process-files-2.png" alt-text="After you run the AzCopy command, click Next: Process files." lightbox="../media/process-files-2.png":::

    When processing is complete, you can go to the review set and view the remediated files.

### Single item error remediation

Sometimes it doesn't make sense to remediate errors in multiple files when you're unsure if any of those files are relevant to the case you're investigating. It also might not make sense to remediate errors before you've had a chance to review the file metadata (such as file location or who had access) to help you make decisions about the relevance. **Single item error remediation** is a feature that enables you to view the metadata of files with a processing error and, if necessary, remediate the error directly in the review set. To learn more about this, please see [single item error remediation](/microsoft-365/compliance/single-item-error-remediation?azure-portal=true).
