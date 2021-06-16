To get organizations started using Advanced eDiscovery, here's a workflow diagram that aligns with common eDiscovery practices. Each of the five steps is introduced in the following sections.

:::image type="content" source="../media/aed-workflow-2e83d77a.png" alt-text="diagram showing the workflow of Advanced eDiscovery.":::
<br><br>

### Step 1. Add custodians to a case

The first step after creating a case is to add custodians. A custodian is a person having administrative control of a document or electronic file that may be relevant to the case. Here are some things that happen (or that you can do) when you add custodians to a case:

 -  Data in the custodian's Exchange mailbox, OneDrive account, and any Microsoft Teams or Yammer groups that the custodian is a member of can be "marked" as custodial data in the case.
 -  Custodian data is reindexed (by a process called Advanced indexing). Reindexing helps optimize the search experience in the next step.
 -  You can place a hold on custodian data. Custodian hold preserves data that may be relevant to the case during the investigation.
 -  You can associate other data sources with a custodian (for example, you can associate a SharePoint site or Microsoft 365 Group with a custodian) so this data can be reindexed, placed on hold, and searched, just like the data in the custodian's mailbox or OneDrive account.
 -  You can use the communications workflow in Advanced eDiscovery to send a legal hold notification to custodians.

**Additional reading.** For more information, see [Work with communications in Advanced eDiscovery](/microsoft-365/compliance/managing-custodian-communications).

### Step 2. Search custodial data sources for data relevant to the case

After you add custodians to a case, use the built-in search tool to search the custodian data locations for data that may be relevant to the case. You use keywords, properties, and conditions to build search queries that return search results with the data that's most likely relevant to the case. You can also:

 -  View search statistics that may help you refine a search query to narrow the results.
 -  Preview the search results to quickly verify whether the relevant data is being found.
 -  Revise a query and rerun the search.

**Additional reading.** For more information, see [Collect data for a case in Advanced eDiscovery](/microsoft-365/compliance/collecting-data-for-ediscovery).

### Step 3. Add data to a review set

Once you've configured and verified that a search returns the expected data, the next step is to add the search results to a review set. When you add data to a review set, items are copied from their original location to a secure Azure Storage location. The data is reindexed again to optimize it for thorough and fast searches when reviewing and analyzing items in the review set. Additionally, you can also add non-Microsoft 365 data into a review set.

**Additional reading.** For more information, see [Add search results to a review set](/microsoft-365/compliance/add-data-to-review-set).

### Step 4. Review and analyze data in a review set

A wide-variety of tools and capabilities can be used to view and analyze the case data in a review set. The goal of this step is to reduce the data set to what is most relevant to the case you're investigating.

The following table displays links to other resources that can provide guidance during the review process.

:::row:::
  :::column:::
    **Resource**
  :::column-end:::
  :::column:::
    **Task**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [View documents](/microsoft-365/compliance/view-documents-in-review-set)
  :::column-end:::
  :::column:::
    View the metadata for each document in a review set, and view the document in its native version or text version.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Create queries and filters](/microsoft-365/compliance/review-set-search)
  :::column-end:::
  :::column:::
    Create search queries using different kinds of search criteria (including the ability to search all file metadata properties). By doing so, you can further refine and cull the case data to what is most relevant to the case.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Create and use tags](/microsoft-365/compliance/tagging-documents)
  :::column-end:::
  :::column:::
    Apply tags to documents in a review set to identify which are responsive (or non-responsive to the case). The tags can then be used when creating search queries to include or exclude the tagged documents.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Annotate and redact documents](/microsoft-365/compliance/view-documents-in-review-set)
  :::column-end:::
  :::column:::
    Use the annotation tool in a review to annotate documents and redact content in documents. A PDF version of an annotated or redacted document can be generated during the review to reduce the risk of exporting the unredacted native version of the document.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    [Analyze case data](/microsoft-365/compliance/analyzing-data-in-review-set)
  :::column-end:::
  :::column:::
    After running analytics on the data in review set, analysis is provided such as near duplicate detection, email threading, and themes. This analysis can help reduce the volume of documents that must be reviewed. Analytics reports can also be generated that summarize the results from the analytics that were run on the data in the review set.
  :::column-end:::
:::row-end:::


### Step 5. Export and download case data

There are three ways to export data from a review set:

 -  **Download native files.** Download a small set of native files using a browser. This method is the quickest way to export a small set of data. This method preserves the native file names. For more information, see [Download documents from a review set](/microsoft-365/compliance/download-documents-from-review-set).
 -  **Download customized data.** Customize what data is exported. This includes exporting file metadata, native files, text files, and redacted documents that have been saved to a PDF file. Once the exported data is prepared, you can download the data from the Export tab to a local computer. For more information, see [Export documents from a review set](/microsoft-365/compliance/export-documents-from-review-set).
 -  **Add to another review set.** Copy data from one review set to a different review set. For more information, see [Add data from one review set to another review set](/microsoft-365/compliance/add-data-to-review-set-from-another-review-set).
