A Microsoft 365 subscription comes with a set of admin roles that you can assign to users in your organization using the Microsoft 365 admin center. Each admin role maps to common business functions. They give people in your organization permissions to do specific tasks in the admin centers.

> [!NOTE]
> The Microsoft 365 admin center lets you manage Azure AD roles and Microsoft Intune roles. However, these roles are a subset of the roles available in the Azure AD portal and the Intune admin center.

### Security guidelines for assigning roles

Because administrators have access to sensitive data and files, it's recommended that you follow these guidelines to keep your organization's data more secure.

:::row:::
  :::column:::
    **Recommendation**
  :::column-end:::
  :::column:::
    **Why is this recommendation important?**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Have two to four global admins
  :::column-end:::
  :::column:::
    A global admin's password can only be reset by another global admin. As such, it's recommended that you have at least two global admins in your organization in the event one of the admins experiences an account lockout.

The global admin has almost unlimited access to your org's settings and most of the data. As such, it's also recommended that you don't have more than four global admins due to the security threat posed from having too many global admins.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Assign the least permissive role
  :::column-end:::
  :::column:::
    Assigning the least permissive role means giving admins only the access they need to get the job done.

For example, if you want someone to reset employee passwords, you shouldn't assign the unlimited global admin role. Instead, you should assign a limited admin role, like Password admin or Helpdesk admin. This guideline will help keep your data secure.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Require multi-factor authentication (MFA) for admins
  :::column-end:::
  :::column:::
    It's a good idea to require MFA for all your users, but admins should definitely be required to use MFA to sign in. MFA makes users enter a second method of identification to verify they are who they say they are.

Admins can have access to customer and employee data. If you require MFA, then even if the admin's password gets compromised, the password is useless without the second form of identification.

When you turn on MFA, the next time the user signs in, they'll need to provide an alternate email address and phone number for account recovery.

  :::column-end:::
:::row-end:::


Users can receive a message in the admin center indicating they don't have permissions to edit a setting or page. They receive this message because they're assigned a role that doesn't have that permission.

### Commonly used Microsoft 365 admin center roles

In the Microsoft 365 admin center, you can go to **Role assignments,** and then select any role to open its detail pane. Select the **Permissions** tab to view the detailed list of what admins assigned that role have permissions to do. Select the **Assigned** or **Assigned admins** tab to add users to roles.

By default, only the most common roles that most organizations use are displayed first. If you can't find a role, go to the bottom of the list and select **Show all by Category**. The following table displays the roles most typically assigned by an organization.

:::row:::
  :::column:::
    **Admin role (alphabetical order)**
  :::column-end:::
  :::column:::
    **Who should be assigned this role?**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Billing admin
  :::column-end:::
  :::column:::
    Assign the Billing admin role to users who make purchases, manage subscriptions and service requests, and monitor service health.

Billing admins also can:
\- Manage all aspects of billing.
\- Create and manage support tickets in the Azure portal.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Compliance admin
  :::column-end:::
  :::column:::
    Assign the Compliance admin role to users who are responsible for helping your organization:
\- Stay compliant with any regulatory requirements.
\- Manage eDiscovery cases.
\- Maintain data governance policies across Microsoft 365 locations, identities, and apps.
\- Monitor compliance-related policies across Microsoft 365 services.
\- Manage compliance alerts.
\- Perform legal and data investigations.
\- Manage Data Subject Requests.
\- View all Intune audit data.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Exchange admin
  :::column-end:::
  :::column:::
    Assign the Exchange admin role to users who need to view and manage your user's email mailboxes, Microsoft 365 groups, and Exchange Online. The Exchange admin is also responsible for managing message flow in Microsoft 365.

Exchange admins can also:
\- Recover deleted items in a user's mailbox.
\- Determine how long deleted email should be retained before it's permanently deleted.
\- Set up mailbox features such as the mailbox sharing policy, which determines how users can share calendar and contacts information with others outside of your organization.
\- Set up, Send As, and Send on Behalf delegates for someone's mailbox; for example, when an executive wants their assistant to have permission to send mail on the executive's behalf.
\- Create shared mailboxes so a group of people can monitor and send email from a common email address.
\- Set up anti-spam and malware filters for the organization.
\- Manage Microsoft 365 Groups.When the Exchange Administrator role is assigned to a user, it's recommended that they also be assigned the Service Administrator role. This way they can see important information in the Microsoft 365 admin center, such as the health of the Exchange Online service, and change and release notifications.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Global admin
  :::column-end:::
  :::column:::
    Assign the Global admin role to users who need global access to most management features and data across Microsoft online services.

Only global admins can:
\- Reset passwords for all users.
\- Add and manage domains.
\- Unblock another global admin.

The person who signed up for Microsoft online services is automatically assigned the Global admin role.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Global reader
  :::column-end:::
  :::column:::
    Assign the global reader role to users who need to view admin features and settings in admin centers that the global admin can view. The global reader admin can't edit any settings.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Groups admin
  :::column-end:::
  :::column:::
    Assign the groups admin role to users who need to manage all groups settings across admin centers, including the Microsoft 365 admin center and Azure Active Directory portal.

Groups admins can:
\- Create, edit, delete, and restore Microsoft 365 groups.
\- Create and update group creation, expiration, and naming policies.
\- Create, edit, delete, and restore Azure Active Directory security groups.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Helpdesk admin
  :::column-end:::
  :::column:::
    Assign the Helpdesk admin role to users who must complete the following tasks:
\- Reset passwords.
\- Force users to sign out.
\- Manage service requests.
\- Monitor service health.

The Helpdesk admin can only help non-admin users and users assigned the following roles:
\- Directory reader
\- Guest inviter
\- Helpdesk admin
\- Message center reader
\- Reports reader

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    License admin
  :::column-end:::
  :::column:::
    Assign the License admin role to users who need to assign and remove licenses from users and edit their usage location.

License admins also can:
\- Reprocess license assignments for group-based licensing.
\- Assign product licenses to groups for group-based licensing.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Office Apps admin
  :::column-end:::
  :::column:::
    Assign the Office Apps admin role to users who must complete the following tasks:
\- Use the Office cloud policy service to create and manage cloud-based policies for Office.
\- Create and manage service requests.
\- Manage the What's New content that users see in their Office apps.
\- Monitor service health.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Password admin
  :::column-end:::
  :::column:::
    Assign the Password admin role to a user who needs to reset passwords for non-administrators and Password Administrators.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Message center reader
  :::column-end:::
  :::column:::
    Assign the Message center reader role to users who must complete the following tasks:
\- Monitor message center notifications.
\- Get weekly email digests of message center posts and updates
\- Share message center posts.
\- Have read-only access to Azure AD services, such as users and groups.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Power Platform admin
  :::column-end:::
  :::column:::
    Assign the Power Platform admin role to users who must complete the following tasks:
\- Manage all admin features for Power Apps, Power Automate, and data loss prevention.
\- Create and manage service requests.
\- Monitor service health.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Reports reader
  :::column-end:::
  :::column:::
    Assign the Reports reader role to users who must complete the following tasks:
\- View usage data and the activity reports in the Microsoft 365 admin center.
\- Get access to the Power BI adoption content pack.
\- Get access to sign-in reports and activity in Azure AD.
\- View data returned by Microsoft Graph reporting API.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Security admin
  :::column-end:::
  :::column:::
    Assign the Security admin role to admins who control your organization's overall security. They do so by managing security policies, reviewing security analytics and reports across Microsoft 365 products, and staying up-to-speed on the threat landscape.

Security admins can also:
\- Manage security threats and alerts.
\- View reports.
\- Monitor and respond to suspicious security activity.
\- Assign roles.
\- Manage machine groups.
\- Configure endpoint threat detection and automated remediation.
\- View, investigate, and respond to alerts.
\- View machines/device inventory.
\- View user, device, enrollment, configuration, and application information in Intune.
\- Define the threshold and duration for lockouts when failed sign-in events happen.
\- Configure custom banned password list or on-premises password protection.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Service Support admin
  :::column-end:::
  :::column:::
    Assign the Service Support admin role as an extra role to admins or users who must complete the following tasks besides their usual admin role:
\- Open and manage service requests.
\- View and share message center posts.
\- Monitor service health.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    SharePoint admin
  :::column-end:::
  :::column:::
    Assign the SharePoint admin role to users who need to access and manage the SharePoint Online admin center.

SharePoint admins can also:
\- Create and delete sites.
\- Manage site collections and global SharePoint settings.
\- Define the user profile policies and settings for the organization, including management of promoted sites.
\- Create Business Connectivity Services (BCS) connections to data sources that are outside the SharePoint Online site.
\- Manage records in place, which means that you can leave a document in its current location on a site, or store records in a specific archive.
\- Customize the search experience for users.
\- Configure SharePoint Online hybrid with an on-premises SharePoint Online site.
\- Use InfoPath Forms Services in SharePoint Online to deploy the organization's forms to its sites, enabling users to fill out these forms in a web browser.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Teams administrator
  :::column-end:::
  :::column:::
    Assign the Teams administrator role to users who need to access and manage the Teams admin center.

Teams administrator can also:
\- Manage and create Microsoft 365 groups.
\- Manage meetings.
\- Manage conference bridges.
\- Manage all org-wide settings, including federation, teams upgrade, and teams client settings.
\- Troubleshoot communication issues within Teams.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    User admin
  :::column-end:::
  :::column:::
    Assign the User admin role to users who must complete the following tasks for all users:
\- Add users and groups.
\- Assign licenses.
\- Manage most users properties.
\- Create and manage user views.
\- Update password expiration policies.
\- Manage service requests.
\- Monitor service health.

The user admin can also complete the following actions:
\- Manage usernames.
\- Delete and restore users.
\- Reset passwords.
\- Force users to sign out.
\- Update (FIDO) device keys.

The user admin can complete these tasks for users who aren't admins and for users assigned the following roles:
\- Directory reader
\- Guest inviter
\- Helpdesk admin
\- Message center reader
\- Reports reader


  :::column-end:::
:::row-end:::


**Additional reading**. For more information, including the Windows PowerShell cmdlets associated with a role, see [Azure AD built-in roles](/azure/active-directory/roles/permissions-reference?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”

Choose the best response for each of the questions below. Then select **Check your answers**.