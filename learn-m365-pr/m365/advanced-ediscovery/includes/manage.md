This module describes Advanced eDiscovery administration in the following areas:

- Permissions and licensing
- Adding or removing members from a case
- Implementing compliance boundaries
- Closing or deleting a case

> [!NOTE]
> The Security & Compliance Center is now Microsoft 365 Defender

## Permissions and licensing

This section explains permissions that a user must have to manage the following:

- Use Advanced eDiscovery
- View custodian audit activity
- Load non-Microsoft 365 data
- Set up Attorney-Client Privilege Detection
- Access Advanced eDiscovery Reports (in Preview)

### Permissions to use eDiscovery

To access Advanced eDiscovery in the Microsoft 365 compliance center, you must assign the user the appropriate permissions. Specifically, a user must be added as a member of the eDiscovery Manager or eDiscovery Administrators role group on the **Permissions** page in the Microsoft 365 Defender portal.

Members of these two role groups can do the following:

- Create new cases.
- Add and remove members to a case.
- Place custodians and content locations on hold.
- Create and edit searches and hold locations.
- Add search results to a review set.
- Analyze data in a review set.
- Export and download results from a case.

Additionally, an eDiscovery Administrator can:

- View all cases that are listed on the Advanced eDiscovery page.
- Manage any case in the organization after they add themselves as a member of the case.
- Access and export case data for any case in the organization.

Because of the broad scope of access, an organization should have only a few admins who are members of the eDiscovery Administrators subgroup.

### Permissions to view custodian audit activity

To view custodian activity in the audit log, you must be assigned the View-Only Audit Logs or Audit Logs role in Exchange Online. By default, these roles are assigned to the Compliance Management and Organization Management role groups on the **permissions** page in [Exchange admin center](https://outlook.office365.com/ecp?azure-portal=true).

:::image type="content" source="../media/exchange-admin-center.png" alt-text="Exchange admin center" lightbox="../media/exchange-admin-center.png":::

To give a user the ability to search the Advanced eDiscovery audit log with the minimum level of privileges, you can create a custom role group in Exchange Online, add the View-Only Audit Logs or Audit Logs role, and then add the user as a member of the new role group.

### Permissions to load non-Microsoft 365 data

Uploading non-Microsoft 365 data using the import feature in Advanced eDiscovery requires an account that is assigned to the eDiscovery Manager role group and added as eDiscovery Administrator.

### Permissions to set up Attorney-Client Privilege Detection

The person who enables Attorney-Client Privilege Detection in your tenant must be assigned to the eDiscovery Administrator role in your organization.

### Permissions to set up compliance boundaries

To run the compliance security filter cmdlets, you must be a member of the Organization Management role group in the Microsoft 365 Defender portal. For more information, see [Permissions in the Microsoft 365 Defender portal](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center?azure-portal=true). You also must connect Windows PowerShell to both the Microsoft 365 Defender portal and to your Exchange Online organization to use the compliance security filter cmdlets. This is necessary because these cmdlets require access to mailbox properties, which is why you have to connect to Exchange Online. 

### Licensing

Microsoft 365 E3 only provides the rights for a user to benefit from core eDiscovery features as illustrated in the table below.

:::image type="content" source="../media/microsoft-365-ediscovery-features.png" alt-text="Microsoft 365 eDiscovery features by plan":::

> [!NOTE]
> Advanced eDiscovery is a capability included with:
>
> - Microsoft 365 E5
> - Microsoft 365 E5 Compliance
> - Microsoft 365 E5 eDiscovery and Audit
>
> Please review [Microsoft 365 licensing guidance for security & compliance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance?azure-portal=true) to identify required licenses for your organization.

## Add or remove members from a case

You can add or remove members to manage who can access the case. However, before a member can access and perform tasks in an Advanced eDiscovery case, you must add the user to the eDiscovery Manager role group on the **Permissions** page in the [Microsoft 365 Defender portal](https://security.microsoft.com?azure-portal=true).

On the **Advanced eDiscovery** page, go to the case that you want to add a member to.

1. Click the **Settings** tab and then click **Select** in the **Access & permissions** tile.
1. Click **Update.**
1. Under **Manage members**, click **Add** to add members to the case. You can also choose to add a role group to the case by clicking **Add** under **Manage role groups**.
1. In the list of people or role groups that can be added as members of the case, select the check box next to the names of the people or role groups that you want to add.
1. After you have selected the people or role groups to add as members of the case, click **Add**.
1. In the **Manage this case** flyout page, click **Save** to save the new list of case members.

 :::image type="content" source="../media/manage-case.png" alt-text="Manage this case flyout page":::

## Compliance boundaries

Compliance boundaries enable you to segment your organization into individual business units or divisions. The ability to implement compliance boundaries are often necessary for multi-national corporations that need to respect geographical borders and regulations, and for governments which are often divided into different agencies.

These logical boundaries allow you to control the following:

- User content locations such as mailboxes, SharePoint sites, and OneDrive accounts that eDiscovery managers and investigators can search.
- The ability to restrict who can access eDiscovery cases used to manage the legal, human resources, or other investigations within your organization.

### Sample scenario

In the example illustrated below, Contoso LTD is a Microsoft 365 organization that consists of two subsidiaries, Fourth Coffee and Coho Winery. Contoso administrators will implement compliance boundaries to enforce the following requirements:

- Fourth Coffee eDiscovery managers and investigators can only search the Exchange mailboxes, OneDrive accounts, and SharePoint sites within the Fourth Coffee agency.
- Coho Winery eDiscovery managers and investigators can only search the Exchange mailboxes, OneDrive accounts, and SharePoint sites within the Coho Winery agency.
- eDiscovery managers and investigators can only see eDiscovery cases in their agency.
- eDiscovery managers and investigators can only access the cases that they are a member of.

 > [!div class = "centered"]
 > :::image type="content" source="../media/compliance-boundaries.png" alt-text="Compliance boundaries":::

### Implement compliance boundaries

Compliance boundaries are defined and managed by using a combination of role groups and [Security & Compliance PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell?azure-portal=true) cmdlets.

#### Create a role group for each agency

Role groups are used to control who can see the eDiscovery cases in the Microsoft 365 Compliance Center. This means that eDiscovery managers and investigators can only see the eDiscovery cases in their agency. Role groups also control who can assign members to an eDiscovery case. This means eDiscovery managers and investigators can only assign members to cases that they themselves are a member of. We recommend that you create a role group by copying the built-in eDiscovery Managers group, adding the appropriate members, and removing roles that may not be applicable to your needs.

To create the role groups, go to the **Permissions** page in the [Microsoft 365 Defender portal](https://security.microsoft.com?azure-portal=true) and create a role group for each team in each agency that will use compliance boundaries and eDiscovery cases to manage investigations.

Using the Contoso compliance boundaries sample scenario, four role groups need to be created and the appropriate members added to each one.

- Fourth Coffee eDiscovery Managers
- Fourth Coffee Investigators
- Coho Winery eDiscovery Managers
- Coho Winery Investigators

#### Create a search permissions filter to enforce the compliance boundary

The **New-ComplianceSecurityFilter** cmdlet is used to create a search permissions filter that controls the content locations that eDiscovery managers and investigators can search. This means eDiscovery managers and investigators in the Fourth Coffee agency can only search content locations in the Fourth Coffee subsidiary. The same restriction applies to the Coho Winery subsidiary.

Here are examples of the two search permissions filters that would be created to support the Contoso compliance boundaries scenario. Both of these examples include a comma-separated filters list, in which the mailbox and site filters are included in the same search permissions filter and are separated by a comma.

```PowerShell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "Site_ComplianceAttribute -eq 'FourthCoffee' -or Site_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee*'" -Action ALL
```

```PowerShell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "Site_ComplianceAttribute -eq 'CohoWinery' -or Site_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery*'" -Action ALL
```

To learn more about each of the `New-ComplianceSecurityFilter` parameters, see [New-ComplianceSecurityFilter](/microsoft-365/compliance/permissions-filtering-for-content-search?azure-portal=true).

The entire process for setting up compliance boundaries involves the following steps:

1. Identify a user attribute to define your agencies, i.e. Company or Department.
1. File a request with Microsoft Support to synchronize the user attribute to OneDrive accounts.
1. Create a role group for each agency.
1. Create a search permissions filter to enforce the compliance boundary.
1. Create an eDiscovery case for intra-agency investigations

 To learn more, see [Set up compliance boundaries for eDiscovery investigations](/microsoft-365/compliance/set-up-compliance-boundaries?azure-portal=true).

### Limitations

Consider the following limitations when managing eDiscovery cases and investigations that use compliance boundaries.

- When creating and running a search, you can select content locations that are outside of your agency. However, because of the search permissions filter, content from those locations isn't included in the search results.
- Compliance boundaries do not apply to holds in eDiscovery cases. That means an eDiscovery manager in one agency can place a user in a different agency on hold. However, the compliance boundary will be enforced if the eDiscovery manager searches the content locations of the user who was placed on hold. That means the eDiscovery manager won't be able search the user's content locations, even though they were able to place the user on hold. Also, hold statistics will only apply to content locations in the agency.
- Search permissions filters aren't applied to Exchange public folders.

## Close or delete a case

When the investigation is completed, you can close or delete the case. In most instances, you will only delete a case when starting over. This is what happens when you close or delete a case:

- If the case contains any content locations on hold, those holds will be turned off. This might result in content being permanently deleted or purged, either by the user or by an automated process, such as a deletion policy.
- Closing a case only turns off the holds that are associated with that case. If other holds are placed on a content location (such as a Litigation Hold, a Preservation policy, or a hold from a different eDiscovery case) those holds will still be maintained.
- The case is still listed on the Advanced eDiscovery page in the Microsoft 365 compliance center. The details, holds, searches, and members of a closed case are retained.
- You can edit a case after it is closed. For example, you can add or remove members, create searches, export search results, and prepare search results for analysis in Advanced eDiscovery. The primary difference between active and closed cases is that holds are turned off when a case is closed.
- You can reopen a case that has been closed. However, any holds that were in place when the case was closed will not be automatically reinstated. After the case is reopened, you will have to go to the **Holds** tab and turn on the previous holds. To turn on a hold, select it to display the flyout page, and then set the **Status** toggle to **On**.
- When you delete a case, all components associated with the case, such as the list of custodians, communications, searches, review sets, and export job are deleted.
- When you delete a case, the case is removed from the list of cases on the **Advanced eDiscovery** page in the Microsoft 365 compliance center.
- You cannot recover or reopen a case that has been deleted.

### Close a case

1. On the **Advanced eDiscovery** page, select the case that you want to close.
1. On the **Settings** tab, under **Case Information**, click **Select**.
1. Click **Close case**.
It might take up to 60 minutes for the closing process to complete.

### Reopen a case

1. On the **Advanced eDiscovery** page, select the case that you want to reopen.
1. On the **Settings** tab, under **Case Information**, click **Select**.
1. Click **Reopen case**.
It might take up to 60 minutes for the closing process to complete.

### Delete a case

1. On the **Advanced eDiscovery** page, select the case that you want to delete.
1. On the **Settings** tab, under **Case Information**, click **Select**.
1. Click **Delete case**.
It might take up to 60 minutes for the closing process to complete.

:::image type="content" source="../media/close-delete.png" alt-text="Case information":::
