In Microsoft 365, administrator roles are used to assign specific administrative functions to users. Each admin role maps to common business functions and gives people permissions to do specific tasks in the Microsoft 365 admin center. Admin roles can be managed in Microsoft 365 using the Microsoft 365 admin center or Windows PowerShell.

Individual service administrators can administer their services on the highest level, while the Global admin role simply includes all these service admin roles. This relationship is shown in the following diagram.

> [!NOTE]
> All service admin roles are included in the Global admin role, not just the four service admin roles shown here. The following diagram illustrates the relationship between the service admin roles and the Global admin role.

:::image type="content" source="../media/global-admin-role-relationships-e0920e52.jpg" alt-text="diagram shows how the Global admin role includes all the service admin roles":::


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

### Assign admin roles in Windows PowerShell

Azure Active Directory PowerShell for Graph (Azure AD PowerShell) is the module IT Pros commonly use to manage their Azure Active Directory, including admin role assignments and maintenance. You should install the AzuerAD module and then connect to it.

There's two pieces of data that are required to assign an admin role to a user:

 -  The object ID of the user.
 -  The object ID of the role.

Once you know this information, you can then use the **Add-AzureADDirectoryRoleMember** cmdlet to assign a user to an admin role.

```powershell
Add-AzureADDirectoryRoleMember -ObjectID <ObjectID of the role> -RefObjectId <ObjectID of the user>
```

You must use the **Get-AzureADUser** cmdlet to display the ObjectID of the user that you want to assign the role to. For example, you would run the following command to retrieve the ObjectID for Patti Fernandez:

```powershell
Get-AzureADUser -ObjectID "PattF@contoso.com"
```

To retrieve the ObjectID of the role, it's important to note that Azure AD PowerShell only displays the admin roles that are "enabled". In other words, the role must either be flagged as enabled (if it has no users assigned to it), or it must have at least one active user assignment. To view the enabled roles, run the **Get-AzureADDirectoryrole** cmdlet.

If the role you want to assign appears in this list, then you can add the enabled role to a user account. However, if the role isn't enabled (it doesn't appear in the list), then you must first enable it before assigning it to a user. Each of these scenarios is covered in the following sections.

#### Add an enabled admin role to a user

Let's assume you want to assign Patti Fernandez to the Helpdesk Administrator role. When you ran the **Get-AzureADDirectoryRole** cmdlet, let's further assume the role appeared in the list of enabled roles.

You can copy the ObjectID for this role and paste it into the **Add-AzureADDirectoryRoleMember** command. Let's assume the ObjectID of the Helpdesk Administrator role in this fictitious scenario is 729827c3-9c14-49f7-bb1b-9608-f156-bbb8.

Similarly, can you copy and paste in the ObjectId for Patti Fernandez's user account after you ran the **Get-AzureADUser** command. In this example, the ObjectID for Patti's user account is a4a9ed46-369c-4b69-9e47-d2ac6029485d.

You would then enter the following command and paste in each of the ObjectId's to assign Patti to the Helpdesk Administrator role:

```Add-AzureADDirectoryRoleMember -ObjectID

```

#### Enable an admin account and then add it to a user

In this scenario, let's assume the Helpdesk Administrator role didn't appear in the list of enabled roles when you ran the **Get-AzureADDirectoryRole** cmdlet. In this event, you should first run the following series of PowerShell commands to enable the Helpdesk Administrator role:

```powershell
# Run the following four steps to enable the Helpdesk Administrator role.

# Step 1 - Run the Get-AzureADDirectoryRoleTemplate command to display the list of templates for all Azure AD roles. You'll enable the Helpdesk Administrator role from the Helpdesk Administrator role template.
Get-AzureADDirectoryRoleTemplate

ObjectId                            DisplayName              Description
--------                            -----------              -----------
f023fd81-a637-4b56-95fd-791ac0226033 Global Administrator    Can manage all aspects of Azure AD and Microsoft services that use Azure AD identities.
b0f54661-2d74-4c50-afa3-1ec803f12efe Billing Administrator  Can perform common billing related tasks like payment information.
75941009-915a-4869-abe7-691bff18279e Guest user              Default role for guest users. Can read a limited set of directory information.
d65e02d2-0214-4674-8e5d-766fb330e2c0 User Administrator      Can manage all aspects of users and groups, including resetting passwords for limited admins.
d405c6df-0af8-4e3b-95e4-4d06e542189e Exchange Administrator  Can manage all aspect of the Exchange product.
95e79109-95c0-4d8e-aee3-d01accf2d47b Helpdesk Administrator  Can reset passwords for non-administrators and Helpdesk Administrators.
and so on...

# Step 2 - Retrieve the Role Template object for the Helpdesk Administrator role in the $HelpdeskRole variable.
$HelpdeskRole = Get-AzureADDirectoryRoleTemplate | Where-Object {$_.DisplayName -eq "Helpdesk Administrator"}

# Step 3 - Display the contents of the $HelpdeskRole variable to verify you found the correct role template.
$HelpdeskRole

ObjectId                            DisplayName              Description
--------                            -----------              -----------
95e79109-95c0-4d8e-aee3-d01accf2d47b Helpdesk Administrator  Can reset passwords for non-administrators and Helpdesk Administrators.

# Step 4 - Enable the directory role that's based on the Helpdesk Administrator role template that's in the $HelpdeskRole variable.
Enable-AzureADDirectoryRole -RoleTemplateId $HelpdeskRole.ObjectId

ObjectId                            DisplayName              Description
--------                            -----------              -----------
03618579-3c16-4765-9539-86d9163ee3d9 Helpdesk Administrator  Can reset passwords for non-administrators and Helpdesk Administrators.
```

When you run the **Enable-AzureADDirectoryRole** command in step 4, it enables the role and displays its ObjectID. You'll copy and paste this ObjectID into the **Add-AzureADDirectoryRoleMember** command. In this example, the ObjectID for the newly enabled role is 03618579-3c16-4765-9539-86d9163ee3d9.

Similarly, can you copy and paste in the ObjectId for Patti Fernandez's user account after you ran the **Get-AzureADUser** command. In this example, the ObjectID for Patti's user account is a4a9ed46-369c-4b69-9e47-d2ac6029485d.

You would then enter the following command and paste in each of the Object IDs to assign Patti to the Helpdesk Administrator role:

```powershell

Add-AzureADDirectoryRoleMember -ObjectID "03618579-3c16-4765-9539-86d9163ee3d9" -RefObjectId "a4a9ed46-369c-4b69-9e47-d2ac6029485d"
```
