In Microsoft 365, administrator roles are used to assign specific administrative functions to users. Each admin role maps to common business functions and gives people permissions to do specific tasks in the Microsoft 365 admin center. Admin roles can be managed in Microsoft 365 using the Microsoft 365 admin center or Windows PowerShell.

The following table describes several of the key admin roles that are available in the Microsoft 365 admin center. The table also provides typical scenarios for when these roles should be assigned to users.

:::row:::
  :::column:::
    

**Administrator role**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
  :::column:::
    

**When to use**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Global Administrator


  :::column-end:::
  :::column:::
    

This role is the ultimate administrator and includes access to all administrative features in Microsoft 365. It's also the only admin role who can assign other admin roles.


  :::column-end:::
  :::column:::
    

It's recommended to only have a limited number of global administrators to reduce the risk to your business.


By default, the person who signs up to buy Microsoft 365 becomes a global admin.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Billing Administrator


  :::column-end:::
  :::column:::
    

Makes purchases, manages subscriptions, manages support tickets, and monitors service health.


  :::column-end:::
  :::column:::
    

Ideal for users of your purchasing department that manage Microsoft 365 licenses.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Dynamics 365 Service Administrator


  :::column-end:::
  :::column:::
    

This role can manage instances in the Dynamics 365 admin center and assign users to manage Dynamics 365 at the tenant level.


  :::column-end:::
  :::column:::
    

Used if you must configure and manage Dynamics 365.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Exchange Service Administrator


  :::column-end:::
  :::column:::
    

Manages mailboxes and anti-spam policies for your business, using the Exchange admin center. Can view all the activity reports in the Microsoft 365 admin center.


  :::column-end:::
  :::column:::
    

Used if you must manage mailbox-related settings and attributes such as mailbox size or mail flow connectors.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Helpdesk Administrator


  :::column-end:::
  :::column:::
    

Resets passwords, manages service requests, and monitors service health. Helpdesk admins are limited to resetting passwords for users only. They can't reset passwords for anyone with an administrator role.


  :::column-end:::
  :::column:::
    

For administrators that must reset passwords or manage service requests.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Power BI Administrator


  :::column-end:::
  :::column:::
    

The Power BI admin role will have access to Microsoft 365 Power BI usage metrics. People assigned this role can control the organization's usage of Power BI features.


  :::column-end:::
  :::column:::
    

For administrators who want to manage Power BI.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Service Support Administrator


  :::column-end:::
  :::column:::
    

Can open support requests with Microsoft and views the service dashboard and message center.


They have “view only” permissions except for opening support tickets and reading them.


  :::column-end:::
  :::column:::
    

This role is ideal for first or second-level support staff that manages Microsoft 365 problems and incidents.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

SharePoint Service Administrator


  :::column-end:::
  :::column:::
    

Manages the document storage for your business using the SharePoint admin center in SharePoint Online. They can also assign other people to be Site Collection administrators and Term Store administrators.


People assigned this role can also view all the activity reports in the Microsoft 365 admin center.


  :::column-end:::
  :::column:::
    

For administrators who must manage SharePoint Online.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

User Management Administrator


  :::column-end:::
  :::column:::
    

Resets passwords, monitors service health, adds and deletes user accounts, and manages service requests. The user management admin can’t delete a global admin, create other admin roles, or reset passwords for global, billing, Exchange, SharePoint, Compliance, and Skype for Business admins.


  :::column-end:::
  :::column:::
    

Good for user helpdesk personnel that manage user-related issues.


  :::column-end:::
:::row-end:::


Individual service administrators can administer their services on the highest level, while the Global admin role simply includes all these service admin roles. This relationship is shown in the following diagram.

> [!NOTE]
> All service admin roles are included in the Global admin role, not just the four service admin roles shown here. This diagram simply illustrates the relationship between the service admin roles and the Global admin role.

:::image type="content" source="../media/global-admin-role-relationships-e0920e52.jpg" alt-text="diagram shows how the Global admin role includes all the service admin roles":::


Additional admin roles such as Compliance Administrator and Company Administrator are available but are managed using either the Security &amp; Compliance admin center or Windows PowerShell. A list of all available admin roles is available by running the **Get-MsolRole** cmdlet in Windows PowerShell.

### Assign admin roles in Microsoft 365

The Microsoft 365 administrator roles aren't mutually exclusive, but they can be combined. One or more admin roles can be assigned to a user, such as the Exchange admin, SharePoint admin, and User Management admin roles.

Admin roles are based on groups held in Azure Active Directory (Azure AD). Even though these groups can't be seen through the Azure AD console, admin roles can be assigned in either the Microsoft 365 admin center or Windows PowerShell.

To assign admin roles in Microsoft 365 admin center, you must sign in using a Global admin account and follow these steps:

1.  In the Admin center, select **Users**, and then select **Active Users**.
2.  On the **Active users** page, choose the user whose administrator role you want to change. The **Properties** page for the user opens.
3.  Next to **Roles**, select **Edit**.
4.  On the **Edit user roles** page, choose one of the following options:
    
     -  User (no administrator access)
     -  Global administrator
     -  Customized administrator (to see a list of admin roles)
5.  In the **Alternative email address** field, you can type an email address that isn't connected to Microsoft 365. This email address is used for important notifications, including resetting your admin password.
6.  To close the **Edit user roles** page, select **Save**.

To use Windows PowerShell to assign admin roles to users, you must first use the **Get-MsolRole** cmdlet to find out the internal admin role name that you want to assign.

You'll then use the **Add-MsolRoleMember** cmdlet to assign that role to a user. For example, the following cmdlet adds the user Holly Spencer to the Exchange administrator role for Contoso:

```
Add-MsolRoleMember -RoleName "Exchange Service Administrator" -RoleMemberEmailAddress "HollyS@contoso.com”

```

> [!CAUTION]
> For some roles, the internal role name is different from the role name displayed in the Microsoft 365 admin center. That's why you should first use the **Get-MsolRole** cmdlet to find out the "official", internal role name when using PowerShell to assign roles to user accounts. If you use a role name that appears in the admin center, the **Add-MsolRoleMember** command will fail if the internal role name is different.

## **Exercise – Interactive demonstration**

Select the following link to complete an interactive demonstration titled: [Assign delegated administrators with Windows PowerShell](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-100/M3-L2-E1-T2/index.html?azure-portal=true).

This simulation guides you through using Windows PowerShell to assign roles in Microsoft 365 and to show which users are assigned to specific roles.
