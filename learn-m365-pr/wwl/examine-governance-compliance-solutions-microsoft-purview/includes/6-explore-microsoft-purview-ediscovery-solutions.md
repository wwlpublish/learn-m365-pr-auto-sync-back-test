Electronic discovery, or eDiscovery, is the process of identifying and delivering electronic information that can be used as evidence in legal cases. You can use eDiscovery tools in Microsoft Purview to search for content in Exchange Online, OneDrive for Business, SharePoint Online, Microsoft Teams, Microsoft 365 Groups, and Yammer teams. In fact, you can:

 -  Search mailboxes and sites in the same eDiscovery search, and then export the search results.
 -  Use Microsoft Purview eDiscovery (Standard) cases to identify, hold, and export content found in mailboxes and sites.
 -  Manage custodians and analyze content by using the feature-rich Microsoft Purview eDiscovery (Premium) solution. To do so, an organization must have an Office 365 E5 or Microsoft 365 E5 subscription (or related E5 add-on subscriptions).

### eDiscovery solutions in Microsoft Purview

Microsoft Purview provides three eDiscovery solutions: Content search, eDiscovery (Standard), and eDiscovery (Premium).

:::image type="content" source="../media/ediscovery-solutions-microsoft-purview-94780fd4.png" alt-text="Diagram showing the key capabilities of the Microsoft Purview eDiscovery tools.":::


 -  **Content search**. The Content search tool searches for content across Microsoft 365 data sources. It then exports the search results to a local computer.
 -  **eDiscovery (Standard)**. eDiscovery (Standard) builds on the basic search and export functionality of Content search. It enables you to create eDiscovery cases and assign eDiscovery managers to specific cases. eDiscovery managers can only access the cases of which they're members. eDiscovery (Standard) also lets you associate searches and exports with a case. It then lets you place an eDiscovery hold on content locations relevant to the case.
 -  **eDiscovery (Premium)**. The eDiscovery (Premium) tool builds on the existing case management, preservation, search, and export capabilities in eDiscovery (Standard). eDiscovery (Premium) provides an end-to-end workflow to identify, preserve, collect, review, analyze, and export content that's responsive to an organization's internal and external investigations. It lets legal teams manage custodians and the legal hold notification workflow to communicate with custodians involved in a case. It allows you to collect and copy data from the live service into review sets. From there, you can filter, search, and tag content to remove non-relevant content from further review. By doing so, your workflow can identify and focus on content that's most relevant. eDiscovery (Premium) provides analytics and machine learning-based predictive coding models to further narrow to scope of your investigation to the most relevant content.

### Comparison of key capabilities

The following table compares the key capabilities available in Content search, eDiscovery (Standard), and eDiscovery (Premium).

| **Capability**                                        | **Content search** | **eDiscovery (Standard)** | **eDiscovery (Premium)** |
|:----------------------------------------------------- |:------------------:|:-------------------------:|:------------------------:|
| Search for content                                    |         X          |             X             |            X             |
| Keyword queries and search conditions                 |         X          |             X             |            X             |
| Search statistics                                     |         X          |             X             |            X             |
| Export search results                                 |         X          |             X             |            X             |
| Role-based permissions                                |         X          |             X             |            X             |
| Case management                                       |                    |             X             |            X             |
| Place content locations on legal hold                 |                    |             X             |            X             |
| Custodian management                                  |                    |                           |            X             |
| Legal hold notifications                              |                    |                           |            X             |
| Advanced indexing                                     |                    |                           |            X             |
| Error remediation                                     |                    |                           |            X             |
| Review sets                                           |                    |                           |            X             |
| Support for cloud attachments and SharePoint versions |                    |                           |            X             |
| Optical character recognition                         |                    |                           |            X             |
| Conversation threading                                |                    |                           |            X             |
| Collection statistics and reports                     |                    |                           |            X             |
| Review set filtering                                  |                    |                           |            X             |
| Tagging                                               |                    |                           |            X             |
| Analytics                                             |                    |                           |            X             |
| Predictive coding models                              |                    |                           |            X             |
| Computed document metadata                            |                    |                           |            X             |
| Transparency of long-running jobs                     |                    |                           |            X             |
| Export to customer-owned Azure Storage location       |                    |                           |            X             |

The eDiscovery capabilities listed in the prior table are summarized in the following list:

 -  **Search for content**. You can search for content that's stored in:
     -  Exchange mailboxes
     -  OneDrive for Business accounts
     -  SharePoint sites
     -  Microsoft Teams
     -  Microsoft 365 Groups
     -  Yammer Teams

    Content generated by other Microsoft 365 apps that store data in mailboxes and sites are also included in these searches.

 -  **Keyword queries and search conditions**. Create KQL keyword search queries to search for content that match query criteria. You can also include conditions to narrow the scope of your search.
 -  **Search statistics**. After you run a search, you can view statistics of the estimated search results, such as the number and total size of items matching your search criteria. Other statistics include the top content locations that contain search results and the number of items that match different parts of the search query.
 -  **Export search results**. Exporting search results to a local computer in your organization is a two-step process:
    1.  When you export search results, items are copied from their original content location in Microsoft 365 to a Microsoft-provided Azure Storage location.
    2.  Then you can download those items to a local computer.
 -  **Role-based permissions**. Use role-based access permissions to control what eDiscovery-related tasks that different users can perform. You can use a built-in eDiscovery-related role group or create custom role groups that assign specific eDiscovery permissions.
 -  **Case management**. eDiscovery cases in eDiscovery (Standard) and eDiscovery (Premium) let you associate specific searches and exports with a specific investigation. You can also assign members to a case to control who can access the case and view the contents of the case.
 -  **Place content locations on legal hold**. Preserve content relevant to your investigation by placing a legal hold on the content locations in a case. Doing so lets you secure electronically stored information from inadvertent (or intentional) deletion during your investigation.
 -  **Custodian management**. Manage the people that you've identified as people of interest in the case (called **custodians**) and other data sources that may not be associated with a custodian. When you add custodians and non-custodial data sources to a case, you can:
     -  Place a legal hold on these data sources.
     -  Communicate with custodians by using the legal hold notification process.
     -  Search custodian and non-custodial data sources to collect content relevant to the case.
 -  **Legal hold notifications**. Manage the process of communicating with case custodians. A legal hold notification instructs custodians to preserve content that's relevant to the case. You can track the notices that were received, read, and acknowledged by custodians. The communications workflow in eDiscovery (Premium) enables you to create and send initial notifications, reminders, and escalations if custodians fail to acknowledge a hold notification.
 -  **Advanced indexing**. When you add custodial and non-custodian data sources to a case, the associated content locations are reindexed (in a process called **Advanced indexing**). In this process, content that's deemed as partially indexed is reprocessed to make it fully searchable when you collect data for an investigation.
 -  **Error remediation**. Fix processing errors using a process called **error remediation**. Error remediation allows you to rectify data issues that prevent eDiscovery (Premium) from properly processing the content during Advanced indexing. For example, files that are password protected can't be processed since the files are locked or encrypted. Using error remediation, you can download files with errors, remove the password protection, and then upload the remediated files.
 -  **Review sets**. Add relevant data to a review set. A review set is a secure, Microsoft-provided Azure Storage location in the Microsoft cloud. When you add data to a review set, the collected items are copied from their original content location to the review set. Review sets provide a static, known set of content that you can search, filter, tag, analyze, and predict relevancy using predictive coding models. You can also track and report on what content gets added to the review set.
 -  **Support for cloud attachments and SharePoint versions**. When you add content to a review set, you can include cloud attachments or linked files. By doing so, the target file of a cloud attachment or linked file is added to the review set. You can also add all versions of a SharePoint document to a review set.
 -  **Optical character recognition (OCR)**. When content is added to a review set, OCR functionality extracts text from images. It also includes the image text with the content that's added to a review set. This process lets you search for image text when you query the content in the review set.
 -  **Conversation threading**. When chat messages from Teams and Yammer conversations are added to a review set, you can collect the entire conversation thread. By doing so, the entire chat conversation that contains items that match the collection criteria is added to the review set. Once this information is in the review set, you review chat items in the context of the back-and-forth conversation.
 -  **Collection statistics and reports**. After you create a draft collection or commit a collection to a review set, you can view a rich set of statistics on the retrieved items. For example, statistics may include the content locations that contain the most items that matched the search criteria and the number of items returned by the search query. You can also preview a subset of the results.
 -  **Review set filtering**. After content is added to a review set, you can apply filters to display only the set of items that match your filtering criteria. Then you can save the filter sets as a query, which lets you quickly reapply the saved filters. Review set filtering and saved queries help you quickly remove content so that you end up with the items that are most relevant to your investigation.
 -  **Tagging**. Tags also help you remove non-relevant content and identify the most relevant content. When experts, attorneys, or other users review content in a review set, their opinions related to the content can be captured by using tags. For example, if the intent is to remove unnecessary content, a user can tag documents with a tag such as "non-responsive". After content has been reviewed and tagged, a review set query can be created to exclude any content tagged as "non-responsive". This process eliminates the non-responsive content from subsequent steps in the eDiscovery workflow.
 -  **Analytics**. eDiscovery (Premium) provides tools to analyze review set documents. This process helps you organize the documents in a coherent manner. It also helps reduce the volume of documents to be reviewed.
     -  **Near duplicate detection** groups textually similar documents together to help you make your review process more efficient.
     -  **Email threading** identifies specific email messages that give a complete context of the conversation in an email thread.
     -  **Themes** functionality attempts to analyze themes in review set documents and assign a theme to documents so that you can review documents with related theme.

    These analytics capabilities help make your review process more efficient. This process enables your reviewers to review a fraction of collected documents.

 -  **Predictive coding models**. Use predictive coding models to reduce large volumes of case content to a relevant set of items that you can prioritize for review. This process is accomplished by creating and training your own predictive coding models that help you prioritize the review of the most relevant items in a review set. The system uses the training to apply prediction scores to every item in the review set. By using predictive coding models, you can filter items based on the prediction score. This filtering process enables you to review the most relevant (or non-relevant) items first.
 -  **Computed document metadata**. Many eDiscovery (Premium) features add metadata properties to review set documents. These features include:
     -  Advanced indexing
     -  Conversation threading
     -  Analytics
     -  Predictive coding

    This metadata contains information related to the function performed by a specific feature. When reviewing documents, you can filter on metadata properties to display documents that match your filter criteria. This metadata can be imported into third-party review applications after review set documents are exported.

 -  **Transparency of long-running jobs**. Jobs in eDiscovery (Premium) are typically long-running processes that are triggered by user actions. Examples of these processes include:
     -  Adding custodians to a case.
     -  Adding content to a review set.
     -  Running analytics.
     -  Training predictive coding models.

    You can track the status of these jobs and get support information if you must escalate issues to Microsoft Support.

 -  **Export to customer-owned Azure Storage location**. When you export documents from a review set, you can export them to an Azure Storage account managed by your organization. Additionally, eDiscovery (Premium) lets you customize what data is exported. This process includes exporting:
     -  file metadata
     -  native files
     -  text files
     -  tags
     -  redacted documents saved to a PDF file

## 

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”