In Microsoft 365, you use administrator roles to assign specific administrative functions to users. Each admin role maps to common business functions and gives people in your organization permissions to do specific tasks in the Microsoft 365 admin center. You can manage admin roles in Microsoft 365 using the Microsoft 365 admin center or Windows PowerShell.

The following table describes several of the key admin roles that are available in the Microsoft 365 admin center. The table also provides typical scenarios for when these roles should be assigned to users.

:::row:::
  :::column:::
    <p><b>Administrator role</b></p>
  :::column-end:::
  :::column:::
    <p><b>Description</b></p>
  :::column-end:::
  :::column:::
    <p><b>When to use</b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Global Administrator</p>
  :::column-end:::
  :::column:::
    <p>This role is the ultimate administrator and includes access to all administrative features in Microsoft 365. It is also the only admin role who can assign other admin roles.</p>
  :::column-end:::
  :::column:::
    <p>It is recommended to only have a limited number of global administrators to reduce the risk to your business.<br></p>  <p>By default, the person who signs up to buy Microsoft 365 becomes a global admin.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Billing Administrator</p>
  :::column-end:::
  :::column:::
    <p>Makes purchases, manages subscriptions, manages support tickets, and monitors service health.</p>
  :::column-end:::
  :::column:::
    <p>Ideal for users of your purchasing department that manage Microsoft 365 licenses.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Dynamics 365 Service Administrator</p>
  :::column-end:::
  :::column:::
    <p>This role can manage instances in the Dynamics 365 admin center and is able to assign users to manage Dynamics 365 at the tenant level.</p>
  :::column-end:::
  :::column:::
    <p>Used if you need to configure and manage Dynamics 365.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Exchange Service Administrator</p>
  :::column-end:::
  :::column:::
    <p>Manages mailboxes and anti-spam policies for your business, using the Exchange admin center. Can view all the activity reports in the Microsoft 365 admin center.</p>
  :::column-end:::
  :::column:::
    <p>Used if you need to manage mailbox-related settings and attributes such as mailbox size or mail flow connectors.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Helpdesk Administrator</p>
  :::column-end:::
  :::column:::
    <p>Resets passwords, manages service requests, and monitors service health. Helpdesk admins are limited to resetting passwords for users only; they cannot reset passwords for anyone with an administrator role.</p>
  :::column-end:::
  :::column:::
    <p>For administrators that need to reset passwords or manage service requests.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Power BI Administrator</p>
  :::column-end:::
  :::column:::
    <p>The Power BI admin role will have access to Microsoft 365 Power BI usage metrics. They'll also be able to control your organization's usage of Power BI features.</p>
  :::column-end:::
  :::column:::
    <p>For administrators that want to manage Power BI.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>Service Support Administrator</p>
  :::column-end:::
  :::column:::
    <p>Can open support requests with Microsoft and views the service dashboard and message center.<br></p>  <p>They have “view only” permissions except for opening support tickets and reading them.</p>
  :::column-end:::
  :::column:::
    <p>This role is ideal for your first or second-level support staff that manages Microsoft 365 problems and incidents.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>SharePoint Service Administrator</p>
  :::column-end:::
  :::column:::
    <p>Manages the document storage for your business using the SharePoint admin center in SharePoint Online. They can also assign other people to be Site Collection administrators and Term Store administrators.<br></p>  <p>People in this role can also view all the activity reports in the Microsoft 365 admin center.</p>
  :::column-end:::
  :::column:::
    <p>For administrators that need to manage SharePoint Online.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>User Management Administrator</p>
  :::column-end:::
  :::column:::
    <p>Resets passwords, monitors service health, adds and deletes user accounts, and manages service requests. The user management admin can’t delete a global admin, create other admin roles, or reset passwords for global, billing, Exchange, SharePoint, Compliance, and Skype for Business admins.</p>
  :::column-end:::
  :::column:::
    <p>Good for your user helpdesk that manages user-related issues.</p>
  :::column-end:::
:::row-end:::


Individual service administrators can administer their services on the highest level, while the Global admin role simply includes all these service admin roles. This relationship is depicted in the following diagram (Note - all service admin roles are included in the Global admin role, not just the four service admin roles shown here. This diagram simply illustrates the relationship between the service admin roles and the Global admin role.

:::image type="content" source="../media/global-admin-role-relationships-e0920e52.jpg" alt-text="diagram shows how the Global admin role includes all the service admin roles":::


Additional admin roles such as Compliance Administrator and Company Administrator are available but are managed using either the Security &amp; Compliance admin center or Windows PowerShell. A list of all available admin roles is available by running the **Get-MsolRole** cmdlet in Windows PowerShell.

### Assign admin roles in Microsoft 365

All admin roles are not mutually exclusive, but they can be combined. You can assign one or more admin roles to a user, such as the Exchange admin, SharePoint admin, and User Management administrator roles.

Admin roles are based on groups held in Azure Active Directory (AAD). Even though you can’t see these groups through the AAD console, you can assign admin roles either in the Microsoft 365 admin center or using Windows PowerShell.

To assign admin roles in Microsoft 365 admin center, you need to login using a Global admin account and follow these steps:

1.  In the Admin center, select **Users**, and then click **Active Users**.
2.  On the **Active users** page, choose the user whose administrator role you want to change. The **Properties** page for the user opens.
3.  Next to **Roles**, click **Edit**.
4.  On the **Edit user roles** page, you can choose the following options:
    
     *  User (no administrator access)
     *  Global administrator
     *  Customized administrator (to see a list of admin roles)
5.  In the **Alternative email address** field, you can type an email address that is not connected to Office 365. This email address is used for important notifications, including resetting your admin password.
6.  To close the **Edit user roles** page, click **Save**.

If you want to use Windows PowerShell to assign admin roles to your users, you need to use the **Get-MsolRole**cmdlet to find out what is the admin role name you want to assign, and then use the **Add-MsolRoleMember** cmdlet to assign the role to a user. For example, the following cmdlet adds the user Stella Carrillo to the Exchange administrator role:

```
Add-MsolRoleMember -RoleName "Exchange Service Administrator" -RoleMemberEmailAddress "StellaC@adatum.com”
```
