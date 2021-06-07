Advanced eDiscovery can help your organization respond to legal matters or internal investigations by discovering data where it lives. You can seamlessly manage eDiscovery workflows by identifying persons of interest and their data sources, seamlessly apply holds to preserve data, and then manage the legal hold communication process. By collecting data from the source, you can search the live Microsoft 365 platform to quickly find what you need. Intelligent, machine learning capabilities such as deep indexing, email threading, and near duplicate detection also help you reduce large volumes of data to a relevant data set.

An organization can have many reasons to respond to legal cases involving certain executives or other employees. For example, it may need to quickly find and keep specific information in the following sources for further investigation:

 -  email
 -  documents
 -  instant messaging conversations
 -  other content locations used by people in their day-to-day work tasks

With Advanced eDiscovery, organizations can better understand their Microsoft 365 data and reduce their eDiscovery costs. Advanced eDiscovery helps organizations to:

 -  analyze unstructured data within Microsoft 365.
 -  conduct more efficient document reviews.
 -  make decisions to reduce data for eDiscovery.
 -  analyze large data sets and find content that’s most relevant to a case.
 -  organize its content, making the legal review process easier and more efficient.

### Advanced eDiscovery capabilities

The following diagram outlines the three high-level capabilities of Advanced eDiscovery in Microsoft 365. These capabilities are examined in greater detail in the following sections.

:::image type="content" source="../media/advanced-ediscovery-capabilities-340f6a2a.png" alt-text="diagram showing the three parts of Advanced eDiscovery capabilities, from discover and collect data in-lace, to manage workflow in one platform, to cull data intelligently":::


#### Discover and collect data in-place

Organizations that traditionally rely on multiple third-party eDiscovery solutions must copy large volumes of data out of Microsoft 365 to process. They also have to host duplicate data. This necessity increases the time to find relevant data and the risk, cost, and complexity of managing multiple solutions.

Advanced eDiscovery in Microsoft 365 lets you discover data at the source and stay within your Microsoft 365 security and compliance boundary. By collecting data in-place from the live system, Advanced eDiscovery reduces the friction of going back to the source. It also reduces unnecessary work of having to find missing content, which often happens when journaling lags in traditional eDiscovery solutions.

Native search and collection capabilities for data in Teams, Yammer, SharePoint Online, OneDrive for Business, and Exchange Online further enhances data discovery. For example, Advanced eDiscovery:

 -  Reconstructs Teams conversations instead of returning individual messages from conversations.<br>
 -  Collects cloud-based content shared with users by use of links or modern attachments in email message and Teams chats.<br>
 -  Has built-in support for hundreds of non-Microsoft 365 file types.<br>
 -  Collects data from third-party sources (such as Bloomberg, Facebook, Slack, and Zoom Meetings) that's imported and archived in Microsoft 365 by data connectors.<br>

#### Manage your workflow in one platform

Advanced eDiscovery can help organizations reduce the number of eDiscovery solutions they must rely on. It provides a beginning-to-end workflow, all which occurs within Microsoft 365. Advanced eDiscovery helps reduce the friction of identifying and collecting potential sources of relevant information by automatically mapping unique and shared data sources to the person of interest (known as a *custodian*).

Advanced eDiscovery also provides reporting and analytics on potentially relevant data before collecting it for analysis and review. Microsoft Graph APIs can also help organizations automate the eDiscovery workflow and extend Advanced eDiscovery for custom solutions.

#### Cull data intelligently

Intelligent, machine learning capabilities in Advanced eDiscovery help organizations reduce the amount of data to review. These intelligent capabilities help reduce and cull large volumes of data to a relevant set. For example, a built-in review set query helps filter only for unique content by identifying near duplicates. This capability can substantially reduce the amount of data to review.

Other machine learning capabilities can further refine and identify relevant data using smart tags and technology assisted review tools like the Relevance modules.

### Alignment with EDRM

The built-in workflow of Advanced eDiscovery aligns with the eDiscovery process outlined by the Electronic Discovery Reference Model (EDRM). EDRM is a framework that outlines standards for the recovery and discovery of digital data. Its goal is to guide organizations when they collect and assimilate electronic data during the legal process, including criminal evidence discovery. The EDRM framework is a conceptual standard for the E-discovery process, as shown in the following diagram.

:::image type="content" source="../media/edrm-workflow-01f5fb0f.png" alt-text="Diagram showing eDiscovery workflow based on the EDRM framework":::
<br><br>(Image source courtesy of edrm.net. The source image was made available under Creative Commons Attribution 3.0 Unported License.)

At a high level, here's how Advanced eDiscovery supports the EDRM workflow:

 -  **Identification**. After potential persons of interest in an investigation are identified, you can add them as custodians (also called data custodians, because they may have information that's relevant to the investigation) to an Advanced eDiscovery case. After users are added as custodians, it's easy to preserve, collect, and review custodian documents.
 -  **Preservation**. To preserve and protect data that's relevant to an investigation, Advanced eDiscovery lets you place a legal hold on the data sources associated with the custodians in a case. You can also place non-custodial data on hold. Advanced eDiscovery also has a built-in communications workflow so you can send legal hold notifications to custodians and track their acknowledgments.
 -  **Collection**. After the data sources relevant to an investigation are identified and preserved, you can use the built-in search tool in Advanced eDiscovery to search for and collect live data from the custodial data sources (and non-custodial data sources, if applicable) that may be relevant to the case.
 -  **Processing**. After all data relevant to the case has been identified, the next step is to process it for further review and analysis. In Advanced eDiscovery, the in-place data that you identified in the collection phase is copied to an Azure Storage location (called a review set). This location provides a static view of the case data.
 -  **Review**. After data has been added to a review set, you can view specific documents and run more queries to reduce the data to what is most relevant to the case. You can also annotate and tag specific documents.
 -  **Analysis**. Advanced eDiscovery provides an integrated analytics tool that helps you further cull data from the review set that you determine isn't relevant to the investigation. Besides reducing the volume of relevant data, Advance eDiscovery also helps you save legal review costs. It does so by letting you organize content to make the review process easier and more efficient.
 -  **Production and Presentation**. When you're ready, you can export documents from a review set for legal review. You can export documents in their native format or in an EDRM-specified format so they can be imported into third-party review applications.

**Additional reading.** For more information, see [Assign eDiscovery permissions in the Security &amp; Compliance Center](/microsoft-365/compliance/assign-ediscovery-permissions).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”