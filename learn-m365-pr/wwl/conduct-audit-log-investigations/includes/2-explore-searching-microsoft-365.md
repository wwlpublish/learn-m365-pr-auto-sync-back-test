The Microsoft 365 compliance center can be used to search the unified audit log to view user and administrator activity in a company's Microsoft 365 tenant. The following types of activity can be searched for in Microsoft 365:

 -  User activity in SharePoint Online and OneDrive for Business.
 -  User activity in Exchange Online (Exchange mailbox audit logging).<br>
 -  Admin activity in SharePoint Online.
 -  Admin activity in Azure Active Directory (the directory service for Microsoft 365).
 -  Admin activity in Exchange Online (Exchange admin audit logging).
 -  User and admin activity in Sway.
 -  User and admin activity in Power BI for Microsoft 365.
 -  User and admin activity in Microsoft Teams.
 -  User and admin activity in Yammer.

> [!TIP]
> Mailbox audit logging must be turned on for each user mailbox before user activity in Exchange Online is logged. For more information, see [Enable mailbox auditing in Office 365](https://support.office.com/article/Enable-mailbox-auditing-in-Office-365-aaca8987-5b62-458b-9882-c28476a66918?azure-portal=true).

Depending on the Microsoft 365 service, it can take anywhere from 30 minutes to 24 hours after an event occurs for the corresponding audit log entry to be displayed in the search results. The following table shows the time it can take for the different services.

|              **Microsoft 365 service**              | **Up to** **30 minutes after an event occurs** | **Up to** **24 hours after an event occurs** |
|::|:-:|:--:|
|    <p>Azure Active Directory (admin events)</p>     |                                                |                   <p>X</p>                   |
| <p>Azure Active Directory (user sign-in events)</p> |                                                |                   <p>X</p>                   |
|               <p>Exchange Online</p>                |                    <p>X</p>                    |                                              |
|               <p>Microsoft Teams</p>                |                    <p>X</p>                    |                                              |
|                   <p>Power BI</p>                   |                                                |                   <p>X</p>                   |
|   <p>Security &amp; Compliance Center</p>           |                    <p>X</p>                    |                                              |
| <p>SharePoint Online and OneDrive for Business</p>  |                    <p>X</p>                    |                                              |
|                     <p>Sway</p>                     |                                                |                   <p>X</p>                   |
|                    <p>Yammer</p>                    |                                                |                   <p>X</p>                   |

### Prerequisites for the audit log search<br>

Microsoft 365 Enterprise admins must enable auditing in their Microsoft 365 tenants before they can begin auditing user activity. The **View-Only Audit Logs** or **Audit Logs** role in Exchange Online must also be assigned to the admins. By default, these roles are assigned to the **Compliance Management** and **Organization Management** role groups on the **Permissions** page in the Exchange admin center.

To give a user the ability to search the Microsoft 365 audit log with the minimum level of privileges, the Enterprise admin can:

 -  create a custom role group in Exchange Online.
 -  add the **View-Only Audit Logs** role or the **Audit Logs** role to the role group.
 -  add the user as a member of the new role group.

> [!WARNING]
> If you assign a user either the **View-Only Audit Logs** role or the **Audit Logs** role on the **Permissions** page in the Microsoft 365 compliance center, they won't be able to search the Microsoft 365 audit log. **The permissions must be assigned in Exchange Online rather than the Microsoft 365 compliance center because the underlying cmdlet used to search the audit log is an Exchange Online cmdlet.**

Enabling auditing in a company's Microsoft 365 tenant is a one-time process. Follow these steps to turn it on:

1.  In the **Security &amp; Compliance Center**, select **Search &amp; investigation** &gt; **Audit log search** in the left navigation pane.
2.  Select **Start recording user and admin activities**.

After audit logging is turned on, a message is displayed that says the audit log is being prepared. The message also indicates that you can run a search in a couple of hours after the preparation is complete.

:::image type="content" source="../media/audit-log-search-window-d1702fab.png" alt-text="screenshot of the Audit Log Search window":::


> [!TIP]
> If you don't see this link, auditing has already been turned on for your organization.

For those admins who prefer to work with PowerShell, you can turn on audit log searching by running the following cmdlet in Exchange Online PowerShell, instead of using the Microsoft 365 compliance center:

```powershell
Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
```

### Audited activities

The following table describes the activities that are audited in Microsoft 365. You can search for these events by searching the audit log within the Microsoft 365 compliance center.

:::row:::
  :::column:::
    

**Audited activity**


  :::column-end:::
  :::column:::
    

**Use it to search for...**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

File and page activities


  :::column-end:::
  :::column:::
    

File and page-related activities in SharePoint Online and OneDrive for Business.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Folder activities


  :::column-end:::
  :::column:::
    

Folder-related activities in SharePoint Online and OneDrive for Business.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Sharing and access request activities


  :::column-end:::
  :::column:::
    

User sharing and access request activities in SharePoint Online and OneDrive for Business.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Synchronization activities


  :::column-end:::
  :::column:::
    

File synchronization activities in SharePoint Online and OneDrive for Business.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Site administration activities


  :::column-end:::
  :::column:::
    

Site administration tasks in SharePoint Online.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Exchange mailbox activities


  :::column-end:::
  :::column:::
    

Mailbox activities completed by the mailbox owner, a delegated user, or an administrator.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Sway activities


  :::column-end:::
  :::column:::
    

User and admin activities in Sway


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

User administration activities


  :::column-end:::
  :::column:::
    

User administration activities that are logged when an admin adds or changes a user account by using the Microsoft 365 admin center or the Azure management portal.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Azure AD group administration activities


  :::column-end:::
  :::column:::
    

Group administration activities that are logged when an admin or a user creates or changes a Microsoft 365 group or when an admin creates a security group by using the Microsoft 365 admin center or the Azure management portal.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Application administration activities


  :::column-end:::
  :::column:::
    

Application admin activities that are logged when an admin adds or changes an application that's registered in Azure AD.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Role administration activities


  :::column-end:::
  :::column:::
    

Azure AD role administration activities that are logged when an admin manages admin roles in the Microsoft 365 admin center or in the Azure management portal.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Directory administration activities


  :::column-end:::
  :::column:::
    

Azure AD directory and domain-related activities that are logged when an administrator manages their Microsoft 365 organization in the Microsoft 365 admin center or in the Azure management portal.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

eDiscovery activities


  :::column-end:::
  :::column:::
    

Content Search and eDiscovery-related activities that are completed in Microsoft 365 Security &amp; Compliance Center or by running the corresponding Windows PowerShell cmdlets.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Power BI activities


  :::column-end:::
  :::column:::
    

User and admin activities in Power BI.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Microsoft Teams activities


  :::column-end:::
  :::column:::
    

User and admin activities in Microsoft Teams.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Yammer activities


  :::column-end:::
  :::column:::
    

User and admin activities in Yammer.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Microsoft Stream


  :::column-end:::
  :::column:::
    

Video activities completed by users, group channel activities, and admin activities such as managing users, managing organization settings, and exporting reports.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Exchange admin activities


  :::column-end:::
  :::column:::
    

Changes in the Exchange Online Organization made by an administrator using the Exchange admin center or by running a cmdlet in Windows PowerShell.


  :::column-end:::
:::row-end:::


**Additional reading.** For detailed information of audited actions, see [Searching the audit log within the Office 365 Security &amp; Compliance Center](https://support.office.com/article/search-the-audit-log-in-the-office-365-security-compliance-center-0d4d0f35-390b-4518-800e-0c7ec95e946c?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”