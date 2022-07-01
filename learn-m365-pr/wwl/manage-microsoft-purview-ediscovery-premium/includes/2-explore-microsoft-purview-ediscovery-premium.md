The Microsoft Purview eDiscovery (Premium) solution builds on the Microsoft Purview eDiscovery (Standard) and analytics capabilities. eDiscovery (Premium) provides an end-to-end workflow to preserve, collect, analyze, review, and export content that's responsive to an organization's internal and external investigations. It also lets legal teams manage the entire legal hold notification workflow to communicate with custodians involved in a case.

### eDiscovery (Premium) capabilities

eDiscovery (Premium) seamlessly builds on the eDiscovery (Standard) feature set to help an organization respond to legal matters or internal investigations by discovering data where it lives. It enables organizations to:

 -  manage eDiscovery workflows by identifying persons of interest and their data sources.
 -  apply holds to preserve data.
 -  manage the legal hold communication process.

By collecting data from the source, an organization can search the live Microsoft 365 platform to quickly find what it needs. With eDiscovery (Premium), an organization can reduce large volumes of data to a relevant data set. It does so by using intelligent, machine learning capabilities, such as:

 -  deep indexing
 -  email threading
 -  near duplicate detection

The following sections describe how the key eDiscovery (Premium) capabilities shown in the following diagram can help an organization.

:::image type="content" source="../media/advanced-ediscovery-capabilities-340f6a2a.png" alt-text="Diagram showing the key capabilities of Microsoft Purview eDiscovery Premium.":::


#### Discover and collect data in-place

Traditionally, organizations that rely on multiple third-party eDiscovery solutions require copying large volumes of data out of Microsoft 365 to process and having to host duplicate data. This necessity increases the time to find relevant data and the risk, cost, and complexity of managing multiple solutions.

Microsoft 365's advanced discovery solution, Microsoft Purview eDiscovery (Premium), enables organizations to discover data at the source and stay within their Microsoft 365 security and compliance boundary. By collecting data in-place from the live system, eDiscovery (Premium) reduces the friction of going back to the source. It also reduces the unnecessary work of having to find missing content, which often happens when journaling lags in traditional eDiscovery solutions.

Data discovery is further enhanced by the native search and collection capabilities for data in Teams, Yammer, SharePoint Online, OneDrive for Business, and Exchange Online. For example, eDiscovery (Premium):

 -  Reconstructs Teams conversations, instead of returning individual messages from conversations.
 -  Collects cloud-based content shared with users by use of links or modern attachments in email message and Teams chats.
 -  Has built-in support for hundreds of non-Microsoft 365 file types.
 -  Collects data from third-party sources (such as Bloomberg, Facebook, Slack, and Zoom Meetings) that's imported and archived in Microsoft 365 by [data connectors](/microsoft-365/compliance/archiving-third-party-data?azure-portal=true).

#### Manage eDiscovery workflow in one platform

eDiscovery (Premium) can help organizations reduce the number of eDiscovery solutions they need to rely on. It provides a streamlined, end-to-end workflow, all which occurs within Microsoft 365. eDiscovery (Premium) helps reduce the friction of identifying and collecting potential sources of relevant information. It does so by automatically mapping unique and shared data sources to the person of interest. This person is known as a custodian, or a data custodian, because they may possess information that's relevant to the investigation. eDiscovery (Premium) also provides reporting and analytics on potentially relevant data prior to collecting it for analysis and review.

Additionally, Microsoft Graph APIs can help organizations automate the eDiscovery workflow. They can also extend eDiscovery (Premium) for custom solutions.

#### Cull data intelligently

Intelligent, machine learning capabilities in eDiscovery (Premium) help organizations reduce the amount of data to review. These intelligent capabilities help reduce and cull large volumes of data to a relevant set. For example, a built-in review set query helps filter only for unique content by identifying near duplicates. This capability can substantially reduce the amount of data to review.

Other machine learning capabilities can further refine and identify relevant data by using smart tags and technology assisted review tools like the Relevance modules.

### eDiscovery (Premium) alignment with the Electronic Discovery Reference Model

The built-in workflow of eDiscovery (Premium) in Microsoft 365 aligns with the eDiscovery process outlined by the Electronic Discovery Reference Model (EDRM).

:::image type="content" source="../media/electronic-discovery-reference-model-v2-941b53d1.png" alt-text="Diagram of the Electronic Discovery Reference Model workflow showing its eDiscovery process.":::


(Image based on the EDRM model on edrm.net)

At a high level, here's how eDiscovery (Premium) supports the EDRM workflow:

 -  **Identification**. After an organization identifies potential persons of interest in an investigation, it can add them as custodians to an eDiscovery (Premium) case. After users are added as custodians, it's easy to preserve, collect, and review custodian documents.
 -  **Preservation**. To preserve and protect data that's relevant to an investigation, eDiscovery (Premium) lets an organization place a legal hold on the data sources associated with the custodians in a case. It can also place non-custodial data on hold. eDiscovery (Premium) also has a built-in communications workflow so an organization can send legal hold notifications to custodians and track their acknowledgments.
 -  **Collection**. After an organization identifies (and preserves) the data sources relevant to its investigation, it can use the built-in search tool in eDiscovery (Premium) to search for and collect live data from the custodial data sources (and non-custodial data sources, if applicable) that may be relevant to the case.
 -  **Processing**. After an organization has collected all data relevant to its case, the next step is to process the data for further review and analysis. In eDiscovery (Premium), the in-place data that was identified in the collection phase is copied to an Azure Storage location (called a review set). Doing so provides a static view of the case data.
 -  **Review**. After data has been added to a review set, an organization can view specific documents. It can then run more queries to reduce the data to what is most relevant to the case. The organization can also annotate and tag specific documents.
 -  **Analysis**. eDiscovery (Premium) provides an integrated analytics tool. This tool helps an organization further cull data from the review set when it determines the data isn't relevant to the investigation. Besides reducing the volume of relevant data, Advance eDiscovery also helps an organization save legal review costs by letting it organize content to make the review process easier and more efficient.
 -  **Production and Presentation**. When an organization's ready, it can export documents from a review set for legal review. Documents can be exported in their native format. They can also be exported in an EDRM-specified format. By doing so, the documents can be imported into third-party review applications.

### Knowledge check<br>

Choose the best response for the following question. Then select “Check your answers.”