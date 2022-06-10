Microsoft Purview Information Barriers are policies in Microsoft 365 that a compliance admin can configure to prevent users from communicating and collaborating with each other. This solution is useful if, for example, one division is handling information that shouldn't be shared with specific other divisions. Another example is when a division needs to be prevented, or isolated, from collaborating with all users outside of the division.

Information barriers are often used in highly regulated industries. They're also commonly used in those organizations with compliance requirements, such as finance, legal, and government.

For OneDrive, information barriers can determine and prevent the following kinds of unauthorized collaborations:

 -  User access to OneDrive or stored content.
 -  Sharing OneDrive or stored content with other users.

### Information barriers modes and OneDrive

When information barriers are enabled on SharePoint and OneDrive, the OneDrive of segmented users are automatically protected with IB policies. Information barriers modes help strengthen access, sharing, and membership of a OneDrive site based on its IB mode and segments associated with the OneDrive.

When an organization uses information barriers with OneDrive, the following IB modes are supported:

| **Mode**        | **Description**                                                                                                                                                                                                                                                                                        |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Open            | When a non-segmented user configures their OneDrive, the site's IB mode is set as **Open**, by default. There are no segments associated with the site.                                                                                                                                                |
| Owner Moderated | When a OneDrive is used for collaboration with incompatible users in the presence of the site owner/moderator, the OneDrive's IB mode can be set as **Owner Moderated**. For more information, see [Owner Moderated site](/onedrive/information-barriers?azure-portal=true). |
| Explicit        | When a segmented user configures their OneDrive within 24 hours of enablement, the site's IB mode is set as **Explicit** by default. The user's segment and other segments that are compatible with the user's segment and with each other get associated with the user's OneDrive.                    |
| Inferred        | When a segmented user's OneDrive is configured so that it can be shared with unsegmented users, the site's IB mode can be set as **Inferred**. This mode is an opt-in mode the SharePoint admin can set on OneDrive of a segmented user.                                                               |

### Sharing files from OneDrive

#### Open

When a OneDrive has no segments and its IB mode as **Open**:

 -  The user can share files and folders based on the information barrier policy applied to the user and the sharing setting for the OneDrive.

#### Owner Moderated

When a site's IB mode is set to **Owner Moderated**:

 -  The option to share with **Anyone with the link** is disabled.
 -  The option to share with **Company-wide link** is disabled.
 -  The site and its content can be shared with existing members.
 -  The site and its content can be shared only by the OneDrive owner per their IB policy.

#### Explicit

When a OneDrive has information barriers segments, and its IB mode is set to **Explicit**:

 -  The option to share with **Anyone with the link** is disabled.
 -  The option to share with **Company-wide link** is disabled.
 -  Files and folders can be shared only with users whose segment matches that of the OneDrive.

#### Inferred

When a OneDrive has information barriers segments, and its IB mode is set to **Inferred**:

 -  The option to share with **Anyone with the link** is disabled.
 -  The option to share with **Company-wide link** is disabled.
 -  Files and folders can be shared with users whose segment matches that of the OneDrive and unsegmented users in the tenant.

### Accessing shared files from OneDrive

#### Open mode

When a user wants to access content in a OneDrive that has no segments, and its IB mode is set to **Open**:

 -  The files must be shared with the user.

#### Owner Moderated mode

When a user wants to access a SharePoint site whose IB mode is set to **Owner Moderated**:

 -  The user has site access permissions.

#### Explicit mode

When a user wants to access content in a OneDrive that has segments, and its IB mode is set to **Explicit**:

 -  The user's segment must match a segment that is associated with the OneDrive.
    
    AND
 -  The files must be shared with the user.

> [!NOTE]
> By default, non-segment users can access shared OneDrive files only from other non-segment users with IB modes as **Open**. They can't access shared files from OneDrive that have segment(s) applied and the IB mode is **Explicit**.

#### Inferred mode

When a segmented user wants to access content in a OneDrive that has segments, and its IB mode is set to **Inferred**:

 -  The user's segment must match a segment that is associated with the OneDrive.
    
    AND
 -  The files must be shared with the user.

When an unsegmented user wants to access content in a OneDrive that has segments, and its IB mode is set to **Inferred**:

 -  The user must have site access permissions.

### Example scenario

The following example illustrates three segments at Contoso: HR, Sales, and Research. An information barrier policy has been defined that blocks communication and collaboration between the Sales and Research segments.

:::image type="content" source="../media/info-barriers-segments-example-33148910.png" alt-text="Diagram showing an example of segments in an organization.":::


With information barriers in OneDrive, when a segment is applied to a user, within 24 hours that segment is automatically associated with the user's OneDrive. Other segments that are compatible with the user's segment and with each other will also get associated with the OneDrive. A OneDrive can have up to 100 segments associated with it. A global or SharePoint admin can manage these segments using PowerShell.

The following table shows the effects of this example configuration at Contoso.

| **Components**                       | **HR users** | **Sales users** | **Research users** | **Non-segment users**                          |
| ------------------------------------ | ------------ | --------------- | ------------------ | ---------------------------------------------- |
| Segments associated with OneDrive.   | HR           | Sales, HR       | Research, HR       | None                                           |
| IB mode on OneDrive.                 | Explicit     | Explicit        | Explicit           | Open                                           |
| OneDrive content can be shared with. | HR only      | Sales and HR    | Research and HR    | Anyone based on the sharing settings selected. |
| OneDrive content can be accessed by. | HR only      | Sales and HR    | Research and HR    | Anyone with whom the content has been shared.  |

### Enable SharePoint and OneDrive information barriers in your organization

Enabling information barriers for SharePoint and OneDrive are configured in a single action. Information barriers for the services can’t be enabled separately. SharePoint Administrators or Global Administrators can enable information barriers in SharePoint and OneDrive in an organization. Complete the following steps to enable information barriers for your organization:

1.  [Download](https://www.microsoft.com/download/details.aspx?id=35588?azure-portal=true) and install the latest version of SharePoint Online Management Shell.
2.  Connect to SharePoint Online as a global admin or SharePoint admin in Microsoft 365.
3.  To enable information barriers in SharePoint and OneDrive, run the following command:
    
    ```powershell
    Set-SPOTenant -InformationBarriersSuspension $false
    ```
4.  After you've enabled information barriers for SharePoint and OneDrive in your organization, wait for approximately 1 hour for the changes to take effect.

If you've enabled information barriers for SharePoint in your organization before March 15, 2022, the default access and sharing control for Implicit mode for Microsoft Teams-connected sites are based on the segments associated with the site.

To enable Microsoft 365 group-membership based access and sharing control for all Implicit mode Teams-connected sites in your tenant, run the following command:

```powershell
Set-SPOTenant -IBImplicitGroupBased $true
```

If you have Microsoft 365 Multi-Geo, you must run this command for each of your geo-locations.

### Manage segments on a user's OneDrive

> [!CAUTION]
> If the segments associated with a user's OneDrive don't match the segment applied to the user, the user won't be able to access their OneDrive. Be careful not to associate any segments with the OneDrive of a non-segment user.

> [!WARNING]
> Any changes you make will be overwritten if the user's segment changes.

To associate a segment with a OneDrive, run the following command in the SharePoint Online Management Shell. A OneDrive can have up to 100 associated segments.

```powershell
Set-SPOSite -Identity <site URL> -AddInformationSegment <segment GUID>
```

For example:

```powershell
Set-SPOSite -Identity https://contoso-my.sharepoint.com/personal/John_contoso_onmicrosoft_com -AddInformationSegment 27d20a85-1c1b-4af2-bf45-a41093b5d111
```

When you add segments to a OneDrive, the site's IB mode is automatically updated to **Explicit**. An error will appear if you attempt to associate a segment that isn't compatible with the existing segments on the OneDrive.

To remove segment from a OneDrive, run the following command.

```powershell
Set-SPOSite -Identity <site URL> -RemoveInformationSegment <segment GUID>
```

For example:

```powershell
Set-SPOSite -Identity https://contoso-my.sharepoint.com/personal/John_contoso_onmicrosoft_com -RemoveInformationSegment 27d20a85-1c1b-4af2-bf45-a41093b5d111
```

If all the segments of a OneDrive site are removed, the IB mode of the OneDrive is automatically updated to **Open**.

#### Effects of changes to user segments

If a user's segment changes, the OneDrive's segment and IB mode will be automatically updated within 24 hours.

Example 1: User's segment updated from Research to Sales. The user's OneDrive will be as follows within 24 hours:

 -  Segment: **Sales, HR**
 -  IB mode: **Explicit**

Example 2: User's segment updated from HR to None. The user's OneDrive will be as follows within 24 hours:

 -  Segment: **None**
 -  IB mode: **Open**

#### Effects of changes to information barrier policies

If a compliance administrator changes an existing policy, the change may affect the compatibility of the segments associated with the OneDrive.

For example, segments that were once compatible may no longer be compatible. A SharePoint admin must change the segments associated with an affected site accordingly. Learn how to create an [information barriers policy compliance report in PowerShell](/sharepoint/info-barriers-report?azure-portal=true).

If a policy changes after files are shared, the sharing links will work only if the user attempting to access the shared files has a segment applied that matches a segment associated with the OneDrive.

### View the segments associated with a user's OneDrive

A global or SharePoint admin can view and change the segments associated with a user's OneDrive.

1.  Connect to the [Security &amp; Compliance Center PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell?azure-portal=true) as a global admin.
2.  Run the following command to get the list of segments and their GUIDs.
    
    ```powershell
    Get-OrganizationSegment | ft Name, EXOSegmentID
    ```
3.  Save the list of segments. The following table identifies the segments for the Contoso scenario that was introduced earlier in this unit.
    
    | **Name** | **EXOSegmentId**                     |
    | -------- | ------------------------------------ |
    | Sales    | a9592060-c856-4301-b60f-bf9a04990d4d |
    | Research | 27d20a85-1c1b-4af2-bf45-a41093b5d111 |
    | HR       | a17efb47-e3c9-4d85-a188-1cd59c83de32 |
4.  If not previously completed, download and install the latest SharePoint Online Management Shell. If you installed a previous version of the SharePoint Online Management Shell, follow the instructions in the [Enable SharePoint and OneDrive information barriers in your organization](/sharepoint/information-barriers#enable-sharepoint-and-onedrive-information-barriers-in-your-organization?azure-portal=true) article.
5.  Connect to SharePoint as a global admin or SharePoint admin in Microsoft 365.
6.  Run the following command:
    
    ```powershell
    Get-SPOSite -Identity <site URL> | Select InformationSegment
    ```
    
    For example:
    
    ```powershell
    Get-SPOSite -Identity https://contoso-my.sharepoint.com/personal/John_contoso_onmicrosoft_com | Select Info
    ```

### Manage the IB mode of a user's OneDrive

To view the IB mode of a OneDrive site, run the following command in the SharePoint Online Management Shell as a SharePoint admin or global administrator:

```powershell
Get-SPOSite -Identity <site URL> | Select InformationBarriersMode
```

For example:

```powershell
Get-SPOSite -Identity https://contoso-my.sharepoint.com/personal/John_contoso_onmicrosoft_com | Select InformationBarriersMode
```

An organization's SharePoint admin or global administrator also has the ability to manage the IB mode of a OneDrive site to meet the needs of the organization with new IB modes.

#### Set the IB mode to Owner Moderated mode

**Owner Moderated** mode allows an incompatible segment user access to a OneDrive. For example, you want to allow HR user's OneDrive to be accessed by both Sales and Research segment users in your tenant. **Owner Moderated** is applicable to a OneDrive site that allows incompatible segment users access to OneDrive in the presence of a moderator/owner. Only the site owner has the capability to invite incompatible segment users on the same site.

To update a OneDrive site IB mode to **Owner Moderated**, run the following PowerShell command:

```powershell
Set-SPOSite -Identity <siteurl> InformationBarriersMode OwnerModerated

```

Owner Moderated IB mode can’t be set on a site with segments. Remove the segments before setting the IB mode as Owner Moderated. Access to an Owner Moderated site is allowed for users who have site access permissions. Sharing of an Owner Moderated OneDrive and its contents is only allowed by the site owner per their IB policy.

#### Set the IB mode to Inferred mode

**Inferred** mode allows unsegmented users to access a OneDrive that's associated with segments. For example, you want to allow HR user's OneDrive to be accessed by HR segment and unsegmented users in your tenant. **Inferred** mode is applicable to a OneDrive site that allows segmented and unsegmented users access to OneDrive.

To update a OneDrive site IB Mode to **Inferred**, run the following PowerShell command:

```powershell
Set-SPOSite -Identity <siteurl> InformationBarriersMode Inferred

```

Inferred IB mode can’t be set on a site without segments. Add segments before setting the IB mode as Inferred.
