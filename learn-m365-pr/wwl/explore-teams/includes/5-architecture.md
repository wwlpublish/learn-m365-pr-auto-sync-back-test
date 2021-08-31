Teams is central to the logical architecture of productivity services in Microsoft 365. Teams is built on Microsoft 365 groups, Microsoft Graph, and the same enterprise-grade security, compliance, and manageability as the rest of Microsoft 365. 


## Dependencies of Microsoft Teams

Teams app capabilities depend on underlying communication and collaboration technologies. When you create a team, here's what gets created:

* A new Microsoft 365 Group
* A SharePoint Online site and document library to store team files
* An Exchange Online shared mailbox and calendar
* A OneNote notebook

The following diagram shows the existing dependencies from Teams to the Office 365 services.

 ‎:::image type="content" source="../media/teams-service-dependencies.png" alt-text="A screenshot of Teams Service Dependencies":::


Teams uses the most effective storage location for different Teams data. The following diagram shows the key data entities and location where data is stored at rest. For example, Teams meeting recordings are saved to SharePoint and OneDrive. 

> [!NOTE]
> If a Teams meeting recording fails to successfully upload to SharePoint or OneDrive, the recording will instead be temporarily saved to Azure Media Services (AMS). Once stored in AMS, no retry attempts are made to automatically upload the recording to SharePoint or OneDrive. Meeting recordings stored in AMS are available for 21 days before being automatically deleted. Users can download the video from AMS if they need to keep a copy.

 ‎:::image type="content" source="../media/teams-storage-locations.png" alt-text="A screenshot of Teams Storage Locations":::


## Governance, security, and compliance for Teams

The Teams architecture enables data governance, security, and compliance capabilities. You can protect Teams data with various security and compliance features in Microsoft 365. This protects against leakage and loss of business data by supporting compliant business processes when discovering sensitive business data. 

‎:::image type="content" source="../media/teams-security-compliance.png" alt-text="A graphic explains Teams Security Compliance":::

## Limits of Microsoft Teams

While Microsoft Teams provides various workloads and features, the architecture is naturally bound to several limits that administrators must be aware of. Refer to the documentation in [Limits and specifications for Microsoft Teams](/microsoftteams/limits-specifications-teams?azure-portal=true).

## Conclusion 

Microsoft Teams is built to combine the already effective workloads of Office 365 with a general information protection strategy. This strategy empowers organizations to use Office 365 capabilities to create efficient business processes that conform to modern security, compliance, and data governance requirements. Administrators need to understand the Teams’ architecture how it provides the link between today’s cloud technology and the modern business needs of organizations.

 

 
