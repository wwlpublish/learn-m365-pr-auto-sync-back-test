In Microsoft 365, a Data Loss Prevention (DLP) policy can identify, monitor, and protect sensitive information in a document. However, many organizations already have a process in place for identifying and classifying sensitive information. This process is based on one of the following sources:

 -  the classification properties in Windows Server File Classification Infrastructure (FCI).
 -  the document properties in SharePoint.
 -  the document properties applied by a third-party system.

A DLP policy simply looks for a specific property name/value pair. Any document property can be used, as long as the property has a corresponding managed property for SharePoint search. For example, a SharePoint site collection may use a content type named **Trip Report** with a required field named **Customer**. Whenever a person creates a trip report, they must enter the customer name. This property name/value pair can also be used in a DLP policy—for example, if you want a rule that blocks access to the document for guests when the Customer field contains Contoso.

Organization can create a DLP policy in Microsoft 365 that recognizes the properties that have been applied to documents by Windows Server FCI or other systems. This design enables DLP policies to be enforced on Office documents with specific FCI or other property values.<br>

:::image type="content" source="../media/apply-dlp-policy-steps-based-on-properties-aa72edac.png" alt-text="graphic showing steps to apply DLP policy based on classification properties":::


### Example scenario

Let’s look at an example scenario to illustrate this concept. Let's assume that an organization creates a DLP policy that uses an FCI classification property. This process involves creating the following properties:

 -  A managed property in SharePoint Online.
 -  The actual policy in a Security and Compliance Center PowerShell session.

In this example, an organization is using FCI on its Windows Server–based file servers. They’re using the FCI classification property named **Personally Identifiable Information.** The possible values for this property are **High**, **Moderate**, **Low**, **Public**, and **Not PII**. Because the organization has implemented Microsoft 365, they want to use their existing FCI classification in their Microsoft 365 DLP policies. Using the Security and Compliance Center, they’ll start with a policy template and then customize it to use the FCI classification.

The organization must first create a managed property in SharePoint Online. This property will map to the crawled property created automatically from the FCI property.

The organization will then create a DLP policy with the following rules. Each rule will use the condition **Document properties contain any of these values**:

 -  **Rule 1: FCI PII content - High**. The first rule restricts access to the document if the FCI classification property **Personally Identifiable Information** equals **High** or **Moderate,** and the document is shared with people outside the organization.
 -  **Rule 2: FCI PII content - Low**. The second rule sends a notification to the document owner if the FCI classification property **Personally Identifiable Information** equals **Low,** and the document is shared with people outside the organization.

### Creating a Managed property in SharePoint

Before you can use a Windows Server FCI property or another property in a DLP policy, you must first create a managed property in the SharePoint admin center. This property is required because:

 -  the search index is built from content and metadata.
 -  Microsoft 365 Data Loss Prevention uses the search crawler to identify, classify, and store sensitive information.

In SharePoint Online and OneDrive for Business, the search index is built up by crawling the content on an organization's sites. The crawler picks up content and metadata from the documents in the form of crawled properties. The search schema helps the crawler decide what content and metadata to pick up. Examples of metadata include the author and the title of a document.

To get the content and metadata from the documents into the search index, the crawled properties must be mapped to managed properties. Only managed properties are kept in the index. For example, a crawled property related to author is mapped to a managed property related to author.

This requirement is important because Microsoft 365 DLP uses the search crawler to identify and classify sensitive information on an organization's sites. It then stores that sensitive information in a secure portion of the search index. When a user uploads a document to Microsoft 365, SharePoint automatically creates crawled properties based on the document properties. But to use an FCI or other property in a DLP policy, that crawled property must be mapped to a managed property so that content with that property is kept in the index.

**Additional reading.** For more information on search and managed properties, see [Manage the search schema in SharePoint Online](https://docs.microsoft.com/sharepoint/manage-search-schema?azure-portal=true).

### Considerations when creating a DLP policy

When you create a DLP policy, the only content that's detected is the content that's newly uploaded and the existing content that's edited. To detect existing content, you must manually reindex your library, site, or site collection. This action will trigger the DLP policy so that it becomes aware of all the content.

In SharePoint Online, content is automatically crawled based on a defined crawl schedule. The crawler picks up content that has changed since the last crawl and updates the index. If you need your DLP policy to protect content before the next scheduled crawl, you can complete the following steps:

1.  On the chosen SharePoint Online site, select **Site contents** from the left pane.
2.  Select **Site Settings** in the upper right corner.
3.  Under **Search**, select **Search and offline availability.**
4.  In the **Reindex site** section, select **Reindex site**.
5.  A warning appears, select **Reindex site** again to confirm. The content will be reindexed during the next scheduled crawl.

> [!WARNING]
> Reindexing a site can cause a massive load on the search system. As a result, an organization should avoid reindexing a site unless its scenario absolutely requires it.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”