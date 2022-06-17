The **Data classification** page within the Microsoft Purview compliance portal provides data classification analytics. These capabilities are provided through the Content explorer and Activity explorer tools. There's a separate tab for each tool on the **Data classification** page:

 -  **Content explorer**. This tab provides visibility into the amount and types of sensitive data in an organization. It also enables users to filter by label or sensitivity type. Doing so displays a detailed view of locations where the sensitive data is stored. It provides admins with the ability to:
     -  index the sensitive documents that are stored within supported Microsoft 365 workloads.
     -  identify the sensitive information they're storing.
     -  identify documents that are classified with sensitivity and retention labels.
 -  **Activity explorer**. This tab shows the activities related to sensitive data and labels. For example, label downgrades, or external sharing that could expose content to risk. Activity Explorer displays the activities that are related to sensitive information that's being used by end users. This data includes:
     -  label activities
     -  data loss prevention (DLP) logs
     -  auto-labeling
     -  Endpoint DLP

Each of these analytical tools is introduced in the following sections.

### License requirements for Content explorer and Activity explorer

Every account that accesses and uses data classification must have a license assigned to it from one of these subscriptions:

 -  Microsoft 365 E5/A5/G5
 -  Microsoft 365 E5/A5/G5/F5 Compliance
 -  Microsoft 365 F5 Security and Compliance
 -  Microsoft 365 E5/A5/F5/G5 Information Protection and Governance
 -  Office 365 E5

### Content explorer

Content explorer shows a current snapshot of the items that have a sensitivity label, a retention label, or have been classified as a sensitive information type in your organization.

#### Required permissions to access items in Content explorer

Access to Content explorer is highly restricted because it lets a user read the contents of scanned files.

> [!IMPORTANT]
> These permissions supersede permissions that are locally assigned to the items, which allows viewing of the content.

There are two roles that grant access to Content explorer. These roles are granted using the Microsoft Purview compliance portal:

 -  **Content Explorer List viewer**. Membership in this role group allows the user to see each item and its location in list view. The data classification list viewer role has been pre-assigned to this role group.
 -  **Content Explorer Content viewer**. Membership in this role group allows the user to view the contents of each item in the list. The data classification content viewer role has been pre-assigned to this role group.

The account(s) an organization uses to access Content explorer must be in one or both of the role groups. These role groups are independent role groups and aren't cumulative. For example, if you want to grant an account the ability to view the items and their locations only, grant Content Explorer List viewer rights. If you want that same account to also be able to view the contents of the items in the list, you must also grant Content Explorer Content viewer rights.

You can also assign either or both of the roles to a custom role group to tailor access to Content explorer.

A Global admin can assign the necessary Content Explorer List Viewer and Content Explorer Content Viewer role group membership.

#### Sensitive information types

A DLP policy can help protect sensitive information, which is defined as a sensitive information type. Microsoft 365 includes [definitions for many common sensitive information types](/microsoft-365/compliance/sensitive-information-type-entity-definitions?azure-portal=true) from across many different regions that are ready for organizations to use. For example, a credit card number, bank account numbers, national ID numbers, and Windows Live ID service numbers.

#### Sensitivity labels

A sensitivity label is simply a tag that indicates the value of the item to an organization. It can be applied manually or automatically. Once applied, the label gets embedded in the document. By doing so, it follows the document everywhere it goes. A sensitivity label enables various protective behaviors, such as mandatory watermarking or encryption.

Sensitivity labels must be enabled for files that are in SharePoint and OneDrive in order for the corresponding data to surface in the **Data classification** page of the Microsoft Purview compliance portal. For more information, see [Enable sensitivity labels for Office files in SharePoint and OneDrive](/microsoft-365/compliance/sensitivity-labels-sharepoint-onedrive-files?azure-portal=true).

#### Retention labels

A retention label enables organizations to define how long a labeled item is kept and the steps to be taken prior to deleting it. They're applied manually or automatically through policies. Retention labels can play a role in helping an organization stay in compliance with legal and regulatory requirements.

#### How to use Content explorer

A user with access to Content explorer should complete the following steps to access it:

1.  In the **Microsoft Purview compliance** portal, select **Data classification** on the navigation pane.
2.  On the **Data classification** page, select the **Content explorer** tab.
3.  If you know the name of the label, or the sensitive information type, you can type that into the filter box.
4.  Alternately, you can browse for the item in the **Sensitive info types** column and select the label from the list.
5.  Selecting a **Sensitive info types** item displays **All locations** for the item in the middle of the page.
6.  Select a location in the **All locations** pane and drill down through the folder structure to the item.
7.  Select the item to open it natively in Content explorer.

#### Export

The export control will create a .csv file that contains a listing of whatever the focus of the pane is.

:::image type="content" source="../media/data-classification-export-control-a8654641.png" alt-text="Screenshot of the data classification Export control that appears on the Content explorer tab in the All locations list.":::


> [!NOTE]
> It can take up to seven days for counts to be updated in content explorer.

#### Filter

The Filter tool appears when you drill down into a location, such as an Exchange or Teams folder, or a SharePoint or OneDrive site.

:::image type="content" source="../media/data-classification-search-tool-a811375a.png" alt-text="Screenshot of the Content explorer search tool that appears when you drill into a location in the All locations pane.":::


The scope of the search tool is displayed in the **All locations** pane. What you can search on varies depending on the selected location.

 -  When Exchange or Teams is the selected location, you can search on the full email address of the mailbox. For example, **user@domainname.com**.
 -  When SharePoint or OneDrive is the selected location, the search tool will appear when you drill down to site names, folders, and files.

You can search on:

| **Value**                                         | **Example**                                                                                             |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| full site name                                    | https://contoso.onmicrosoft.com/sites/sitename                                                          |
| file name                                         | RES\_Resume\_1234.txt<br><br>Note: Segments of this file name are the basis of the next three examples. |
| text at the beginning of acfile name              | RES                                                                                                     |
| text after an underscore character in a file name | Resume or 1234                                                                                          |
| file extension                                    | txt                                                                                                     |

### Activity explorer

On the **Data classification** page, the **Overview** and **Content explorer** tabs give you visibility into what content has been discovered and labeled, and where that content is. The **Activity explorer** tab rounds out this suite of data classification analytics tools.

It enables an organization to monitor what's being done with its labeled content. Activity explorer also provides a historical view of activities on an organization's labeled content. The activity information is collected from the Microsoft 365 unified audit logs. It's then transformed and made available in the Activity explorer UI. Activity explorer reports on up to 30 days worth of data.

:::image type="content" source="../media/data-classification-activity-explorer-1-842114de.png" alt-text="Screenshot of the Activity explorer tool showing the Filter control and a sample bar chart for a fictitious company.":::


There are over 30 different filters available for use, including:

 -  Date range
 -  Activity type
 -  Location
 -  User
 -  Sensitivity label
 -  Retention label
 -  File path
 -  DLP policy

#### Required permissions to access Activity explorer

To access Activity explorer, a user must be explicitly assigned membership in any one of the following role groups or explicitly granted one of the following roles.

The list of applicable roles includes:

 -  Information Protection Admin
 -  Information Protection Analyst
 -  Information Protection Investigator
 -  Information Protection Reader

The list of applicable role groups includes:

 -  Information Protection
 -  Information Protection Admins
 -  Information Protection Analysts
 -  Information Protection Investigators
 -  Information Protection Readers

Microsoft 365 role groups include:

 -  Global administrator
 -  Compliance administrator
 -  Security administrator
 -  Compliance data administrator

Microsoft 365 roles include:

 -  Compliance administrator
 -  Security administrator
 -  Security Reader

#### Activity types

Activity explorer gathers activity information from the audit logs on multiple sources of activities. For more detailed information on what labeling activity makes it to Activity explorer, see [Labeling events available in Activity explorer](/microsoft-365/compliance/data-classification-activity-explorer-available-events?azure-portal=true).

The source of activities includes:

 -  Sensitivity label activities and Retention labeling activities from Office native applications
 -  Azure Information Protection add-in
 -  SharePoint Online
 -  Exchange Online (sensitivity labels only)
 -  OneDrive

Examples of activities from these various sources include:

 -  Label applied
 -  Label changed (upgraded, downgraded, or removed)
 -  Autolabeling simulation
 -  File read

Examples of Azure Information Protection (AIP) scanner and AIP client activities include:

 -  Protection applied
 -  Protection changed
 -  Protection removed
 -  Files discovered

Activity explorer also gathers DLP policy match events from Exchange Online, SharePoint Online, OneDrive, Teams Chat and Channel (preview), on-premises SharePoint folders and libraries, on-premises file shares, and Windows 10 and 11 devices through Endpoint data loss prevention (DLP). Some example events from Windows 10 and 11 devices are file:

 -  Deletions
 -  Creations
 -  Copied to clipboard
 -  Modified
 -  Read
 -  Printed
 -  Renamed
 -  Copied to network share
 -  Accessed by unallowed app

Understanding what actions are being taken with your sensitive labeled content helps you see if the controls that you have in place, such as Microsoft Purview Data Loss Prevention policies are effective. If they aren't effective, or if you discover something unexpected, such as a large number of items that are labeled highly confidential and are downgraded general, you can manage your various policies and take new actions to restrict the undesired behavior.

> [!NOTE]
> Activity explorer doesn't currently monitor retention activities for Exchange Online.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”