## OneDrive

OneDrive is a cloud- based service that enables you to store and protect files, share files with others, access files from anywhere using an app or web-browser, and restore all files to a previous date and time. You can easily and securely store and access your files from all your devices. You can work with others regardless of whether they're inside or outside your organization and terminate that sharing whenever you want. OneDrive helps protect your work through advanced encryption while the data is in transit and at rest in data centers.

## Why deploy OneDrive

Most of the advanced enterprise-focused features in OneDrive are available for every subscription type, enabling companies to use OneDrive in whatever way benefits their business the most – whether that's simply a cloud-based file share for a small business or a highly utilized storage system that provides the basis for all collaboration within an enterprise. At its core, however, OneDrive enables you to securely share and work together on all your files. With OneDrive, you can:

- **Access files from all your devices.** Access all your personal files and those files others share with you on all your devices, including mobile, Mac, PC, and in a web browser.
- **Share inside or outside your organization.** Securely share files with people inside or outside your organization by using their email address, even if they don't have a Microsoft Services Account. This common sharing experience is available in the web, mobile, and desktop versions of OneDrive.
- **Collaborate with deep Microsoft Office integration.** Document coauthoring is available in the Office web apps, Office mobile apps, and Office desktop apps, helping you maintain a single working version of any file. Only OneDrive provides coauthoring capabilities in Office apps across all your devices.
- **Quickly find files that matter most.** Finding content in your OneDrive is simplified through the intelligence of the Microsoft Graph application programming interface. This technology simplifies finding what's important by providing file recommendations based on your relationship to other people, how you received various files, and when you last accessed them.
- **Protect your files with enterprise-grade security.** OneDrive has many security and compliance features, enabling you to meet some of the strictest compliance requirements out there.

## Key OneDrive features

The features listed in this section address common customer concerns or specific compliance requirements, or provide unique functionality available only in OneDrive:

- **Known Folder Move.** Makes it easier to move files in your users' Desktop, Documents, and Pictures folders to OneDrive. This lets users continue working in the folders they're familiar with and access their files from any device.
- **OneDrive Files On-Demand**. Enables users to view, search for, and interact with files stored in OneDrive from within File Explorer, without downloading them all to their device. This feature provides a seamless look and feel for both OneDrive and local files, without taking up space on the local hard drive.
- **Modern attachments.** OneDrive integrates with Outlook to allow seamless sharing of OneDrive files that appear just like email attachments. This feature provides a familiar sharing experience but centralizes storage of attachments in OneDrive. It provides collaborative benefits such as version control that’s typically lost when users email documents back and forth.
- **Real-time team collaboration.** Coauthoring in full versions of Microsoft Word, Excel, and PowerPoint.
- **OneDrive files restore.** Enables users to restore files to any point over the past 30 days. To select the desired recovery time, OneDrive presents users with a histogram that shows file activity so they can determine which recovered time meets their needs. From there, users just select the file history entry to which they want to restore, and all changes after that point will be rolled back.
- **Recycle bin**. A recycle bin similar to the one available on the Windows desktop. Deleted files are moved to the recycle bin and kept for a designated time before being permanently deleted. For work or school accounts, deleted files are purged after 93 days unless configured otherwise.
- **Auditing and reporting.** Detailed reporting and auditing capabilities for files OneDrive stores, as well as for files stored through other services, such as Microsoft SharePoint. You can also audit individual file actions, including downloads, renames, and views.
- **Encryption of data in transit and at rest.** OneDrive uses advanced data encryption methods between your client and the data center, between servers in the data center, and at rest. At rest, OneDrive uses disk encryption through BitLocker Drive Encryption and file encryption to secure your data. Each file is encrypted with its own encryption key; anything larger than 64 KB is split into individual chunks, each of which has its own encryption key locked in a key store.
- **Customer-controlled encryption keys.** By using an Office 365 feature called service encryption with Customer Key, you can upload your own encryption keys to Azure Key Vault. Use these keys for encrypting your data at rest in Azure data centers. Even though this encryption is done natively through BitLocker, customers might require the use of their own key to meet security compliance requirements. Should users lose their key, they can retrieve a deleted key from the recycle bin for up to 90 days (based on your configuration).
- **Microsoft 365 Customer Lockbox.** If a Microsoft support engineer needs to access your data to resolve an issue, they must obtain approval from a Microsoft manager first. The Office 365 Customer Lockbox feature adds a requirement to that process: you must approve or reject that access before the support engineer can access your data. With Customer Lockbox, you also set boundaries on how long the engineer can access your data, and all activity during that time is logged for auditing purposes.
- **OneDrive Multi-Geo storage locations.** Multi-Geo is an Office 365 feature that allows organizations to span their storage over multiple Office 365 geo locations and specify in which of those to store users' data. You designate storage geographies on a per-user basis. For multinational customers with data residency requirements, you can use this feature to ensure that each user's data is stored in the geo location necessary for compliance.
- **Government cloud.** OneDrive is available in Office 365 US Government plans. For info about these plans, see [Office 365 US Government](https://products.office.com/government/office-365-web-services-for-government).

## Deployment and management options

You can deploy and manage OneDrive in many ways, but certain options make more sense in larger organizations than in smaller businesses and vice versa. For example, it likely wouldn't make sense to have an enterprise management solution like Microsoft Endpoint Configuration Manager for a business that has just 10 employees. Table 1 outlines the deployment and management tools typically used for small businesses, medium-sized businesses, and enterprises.

**Note**: Keep in mind that an organization in one size category would probably incorporate additional options from other size categories. This table is not intended to exclusively identify a technology with a specific business size.

|      Size of organization     |      Deployment tools used                                                        |      Management                                                                                        |
|-------------------------------|-----------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
|     Small business            |     Local installation                                                            |     OneDrive admin center                                                                              |
|     Medium-sized business     |     Scripted installation or   Microsoft Intune mobile device management (MDM)    |     Office 365 with MDM, OneDrive   admin center, Intune mobile application management (MAM) or MDM    |
|     Enterprise                |     Microsoft Endpoint Manager   with Intune or Windows Autopilot                 |     Microsoft Endpoint   Configuration Manager, Group Policy Objects (GPOs), and so on                 |

Depending on where your organization fits in this table and the technologies available to you, you can choose which portion of this guide to use. For example, if you run a small business, you may want to keep your OneDrive deployment simple by installing the sync app manually on your employees' computers and using the OneDrive admin center to manage a few settings for your users. Alternatively, if you're running an enterprise, you may choose to deploy and manage OneDrive by using advanced tools like Microsoft Endpoint Configuration Manager and Group Policy, and you could use the sections that correspond to those tools, instead. To accommodate various situations, the deployment and management portions of this guide are in a modular format so that you can consume the document in the way that best aligns with your deployment needs and capabilities. This format also provides visibility into alternate technologies to improve your current processes.

### Prerequisites

- **Client and app requirements.** Even though you can upload, download, and interact with your OneDrive files from a web browser, the ideal OneDrive experience comes from the Windows and Mac sync apps, and the iOS and Android mobile apps. With that in mind, OneDrive is available for most operating systems and browsers, and requires minimal hardware.
- **License requirements.** There are multiple methods by which you can acquire a license for OneDrive. However, a few OneDrive features are available only within certain licensing models. For info about the licensing requirements for OneDrive, its advanced features, and any special licensing required for them, see [Office 365 plans](https://www.microsoft.com/microsoft-365/onedrive/online-cloud-storage).

### Preparing your environment

Before you deploy OneDrive, prepare your environment

### Network utilization

A variety of factors can impact the amount of network bandwidth used by OneDrive. For the best experience, we recommend that you assess this impact before doing a full OneDrive deployment across your organization.

### Multi-Geo

If you have data residency requirements, consider OneDrive Multi-Geo. With OneDrive Multi-Geo, you can specify a preferred data location (PDL), from available locations around the world, for each user's OneDrive. For detailed information about OneDrive Multi-Geo, see [Multi-Geo Capabilities in OneDrive and SharePoint in Microsoft 365](/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365/).

Users who have started using OneDrive, either before or after you configure OneDrive Multi-Geo, are supported.

Features such as file sync and mobile device management work normally in a multi-geo environment. There's no special configuration or management.

Key decisions:

- Do you plan to use OneDrive Multi-Geo?
- Will you have OneDrive Multi-Geo fully configured before your users start using OneDrive?

### Hybrid

If you currently use OneDrive or MySites in SharePoint Server on-premises, we highly recommend deploying hybrid OneDrive. With hybrid OneDrive, users are redirected from their on-premises OneDrive to OneDrive in Microsoft 365. Hybrid OneDrive allows for seamless navigation to OneDrive in the cloud from both SharePoint on-premises and Microsoft 365.

If you don't use OneDrive in SharePoint Server, but you do have an on-premises SharePoint environment, you may still want to consider deploying hybrid OneDrive. Doing so will update the OneDrive navigation links in SharePoint Server to point to OneDrive in Microsoft 365 – again, giving your users seamless navigation to OneDrive in the cloud from either location.

### Activity

> [!VIDEO https://mslearn.cloudguides.com/guides/Migrate%20Windows%20known%20folders%20to%20OneDrive]
