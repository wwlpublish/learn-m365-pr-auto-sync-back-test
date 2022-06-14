For SharePoint, information barriers (IBs) can determine and prevent the following kinds of unauthorized collaborations:

 -  Adding a user to a site.
 -  User access to a site or site content.
 -  Sharing a site or site content with other users.

Information barriers modes help strengthen access, sharing, and membership of a site based on its IB mode and any segments associated with the site. When an organization uses information barriers with SharePoint, the following IB modes are supported:

| **Mode**                  | **Description**                                                                                                                                                                                                                                                         | **Examples**                                                                                                       |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Open                      | When a SharePoint site doesn't have segments, the site's IB mode is automatically set as **Open**.                                                                                                                                                                      | A Team site that's created for the company's annual picnic.                                                        |
| Owner Moderated (preview) | When a SharePoint site is created for collaboration between incompatible segments moderated by the site owner, the site's IB mode should be set as **Owner Moderated**. This mode is currently supported only for sites that aren't connected to a Microsoft 365 group. | A site that's created for collaboration between VP of Sales and Research in the presence of VP of HR (site owner). |
| Implicit                  | When a site is provisioned by Microsoft Teams, the site's IB mode is set as **Implicit** by default. A SharePoint admin or global admin can't manage segments with the **Implicit** mode configuration.                                                                 | A Team is created for all Sales segment users to collaborate with each other.                                      |
| Explicit                  | When a segment is added to a SharePoint site either through the end-user site creation experience or by a SharePoint admin adding segment to a site, the site's IB mode is set as **Explicit**.                                                                         | A research site is created for Research segment users.                                                             |

### Sharing sites for IB modes

#### Open

When a site has no segments, and its IB mode is set to **Open**:

 -  The site and its contents can be shared based on the information barrier policy applied to the user. For example, if a user in HR is allowed to communicate with users in Research, the user can share the site with those users.

#### Owner Moderated

When a site's IB mode is set to **Owner Moderated**:

 -  The option to share with **Anyone with the link** is disabled.
 -  The option to share with **Company-wide link** is disabled.
 -  The site and its content can be shared with existing members.
 -  The site and its content can be shared only by the site owner per their IB policy.

> [!NOTE]
> **Owner Moderated** mode is only supported for non-group connected sites.

#### Implicit

When a site's IB mode is set to **Implicit**:

 -  The option to share with **Anyone with the link** is disabled.
 -  The option to share with **Company-wide link** is disabled.
 -  The site and its content can be shared with existing members through a sharing link.
 -  New users can't be directly added to the site. The Team owner should add users to the Team's group using Microsoft Teams.

#### Explicit

When a site is associated with segments, and its IB mode is set to **Explicit**:

 -  The option to share with **Anyone with the link** is disabled.
 -  The option to share with **Company-wide link** is disabled.
 -  The site and its content can be shared only with users whose segment matches that of the site. For example, if a site is associated with the HR segment, the site can be shared with just HR users. This limitation on sharing occurs even though HR is compatible with both Sales and Research segments.
 -  New users can be added as site members only if their segment matches the segment of the site.

### Access control for IB modes

#### Open mode

When a user wants to access a SharePoint site that has no segment, and its IB mode is set to **Open**:

 -  The user has site access permissions.

#### Owner Moderated mode

When a user wants to access a SharePoint site whose iIB mode is set to **Owner Moderated**:

 -  The user has site access permissions.

> [!NOTE]
> **Owner Moderated** mode is only supported for non-group connected sites.

#### Implicit mode

When a user wants to access a SharePoint site whose IB mode is set to **Implicit**:

 -  The user must be a member of the Microsoft 365 group connected to the site.
 -  The user won't have access to the site if they aren't a member of the Microsoft 365 group connected to the site.
 -  The information barriers compliance assistant ensures the group membership is IB compliant.

#### Explicit mode

When a user wants to access a SharePoint site that has segments, and its IB mode is **Explicit**:

 -  The user's segment must match a segment that's associated with the site.
    
    AND
 -  The user must have access permission to the site.

> [!NOTE]
> Non-segment users can't access a site associated with segments. They'll receive an error message.

### Example scenario

The following example illustrates three segments at Contoso: HR, Sales, and Research. An information barrier policy has been defined that blocks communication and collaboration between the Sales and Research segments. These segments are incompatible.

:::image type="content" source="../media/info-barriers-segments-example-33148910.png" alt-text="Diagram showing an example of segments in an organization.":::


With SharePoint information barriers, a SharePoint or global admin can associate segments to a site. Doing so prevents the site from being shared with or accessed by users outside those segments. Up to 100 compatible segments can be associated with a site. The segments are associated at the site level (previously called site collection level). The Microsoft 365 group connected to the site is also associated with the site's segment.

In this example, the HR segment is compatible with both Sales and Research. However, because the Sales and Research segments are incompatible, they can't be associated with the same site.

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

### Site creation and management by site owners

When a segmented user creates a SharePoint site:

 -  The site is associated with the user's segment.
 -  The site's information barriers mode is automatically set to **Explicit**.

When a SharePoint site's IB mode is set to **Explicit,** the site owners can add more segments to the site even if it already has segments. Site owners can't remove added segments from sites. SharePoint admins will have to remove added segments in an organization, if needed.

When a non-segmented user creates a SharePoint site:

 -  The site isn't associated with any segment.
 -  The site's information barriers mode is automatically set to **Open**.

When a SharePoint admin creates a SharePoint site from the SharePoint admin center:

 -  The site isn't associated with any segment.
 -  The site's information barriers mode is automatically set to **Open**.

> [!TIP]
> To help site owners add a segment to a site, share the [Associate information segments with SharePoint sites](https://support.microsoft.com/office/associate-information-segments-with-sharepoint-sites-2b03db07-6d3f-4297-a388-b943317a26a7?azure-portal=true) article with your SharePoint site owners.

### Microsoft Teams sites

When a team is created in Microsoft Teams, a SharePoint site is automatically created for the team's files. To protect the Microsoft Team sites with information barriers control, an organization can enable information barriers in SharePoint for its tenant. Within 24 hours, the site's information barriers mode is automatically set as **Implicit.** Segments associated with the team's members are also associated with the site.

Microsoft Teams sites whose information barrier modes are set to **Implicit** have site access and sharing based on Microsoft 365 group membership. For example, users have access to the Microsoft Teams site if they're members of the Microsoft 365 group connected to the site. The Microsoft 365 group connected to the Team is IB compliant.

> [!NOTE]
> If you have enabled information barriers for SharePoint in your organization before March 15, 2022, the Teams-connected site's access and sharing is based on the segments of the site. For example:

 -  The site and its content can be shared with user whose segment matches that of the site.
 -  The site and its content can be accessed by a user if they have the same segment as the site and the user has site access permissions.

To enable Microsoft 365 group membership-based access and sharing control for all **Implicit** mode sites in an organization, run the following command as a SharePoint Administrator:

```powershell
Set-SPOTenant -IBImplicitGroupBased $true
```

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”