Using IRM in SharePoint Online and Exchange Online supports a wide range of automated encryption and management of sensitive data. It does so without consuming advanced features of Azure Information Protection that need other licenses. Although it provides more granular control over documents, IRM is limited in both function and supported file types, and it’s not a recommended approach to classifying sensitive data.

### Limitations of SharePoint Online IRM

There are certain limitations when working with IRM protected content in SharePoint Online, including:

 -  You can't use the default or custom protection templates that you manage in the Azure portal.
 -  Files that have a .ppdf file name extension for **protected PDF** files aren't supported. Files that have .pdf file name extension are supported and when downloaded, can be opened by a PDF application that natively supports Rights Management.
 -  Coauthoring - when more than one person edits a document at the same time - is not supported. To edit a document in an IRM-protected library, you must first check out the document and download it, and then edit it in your Office application. As a result, only one person can edit the document at a time.

### Differences between IRM and AIP

IRM in SharePoint and Exchange processes IRM protection to emails, documents, and files directly inside the service. Conversely, while Azure Information Protection (AIP) uses IRM mechanisms as well, it primarily works on the client-side. As a result, the AIP client doesn't require any SharePoint Protectors to process documents and files, and it supports far more file types.

For example, the AIP client for Windows includes a viewer for protected PDF files (.ppdf). Alternative PDF viewers are also listed in the RMS-enlightened applications table.

It's also possible to apply RMS templates embedded in AIP labels to protect Office documents that are located inside SharePoint libraries.
