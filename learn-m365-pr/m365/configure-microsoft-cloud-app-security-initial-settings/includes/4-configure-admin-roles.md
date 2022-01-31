It's important for Contoso IT staff to be able to manage which administrative user accounts can perform which administrative tasks in Microsoft Defender for Cloud Apps. To help with this requirement, Defender for Cloud Apps implements Role-based access control (RBAC).

## What is RBAC?

RBAC is an approach to administration that can help make your organization more secure. When you implement RBAC, you assign administrative users to one or more roles. These roles have only the privilege they require to perform specified tasks.

You can take two approaches when configuring RBAC in Defender for Cloud Apps. These are:

- Use the built-in RBAC roles from Office 365 and Azure AD.
- Use Cloud App Security admin roles.  

## Use Office 365 and Azure AD roles in Defender for Cloud Apps

You can use the built-in Office 365 and Azure AD admin roles to manage Defender for Cloud Apps. These roles are described in the following table.

| Role                           | Description                                                  |
| ------------------------------ | ------------------------------------------------------------ |
| Global  administrator          | Admins with  Full access have full permissions in Defender for Cloud Apps. They can add admins,  add policies and settings, upload logs and perform governance actions. |
| Security  administrator        | Admins with  Full access have full permissions in Defender for Cloud Apps. They can add admins,  add policies and settings, upload logs and perform governance actions. |
| Compliance  administrator      | Has read-only  permissions and can manage alerts. Cannot access Security recommendations for  cloud platforms. Can create and modify file policies, allow file governance  actions, and view all the built-in reports under Data Management. |
| Compliance  data administrator | Has read-only  permissions, can create and modify file policies, allow file governance  actions, and view all discovery reports. Cannot access Security  recommendations for cloud platforms. |
| Security  operator             | Has read-only  permissions and can manage alerts.            |
| Security  reader               | Has read-only  permissions and can manage alerts. Is also restricted from performing certain  actions, including: creating policies or edit and change existing ones,  performing any governance actions, uploading discovery logs, and banning or  approving third-party apps. |
| Global reader                  | Has full  read-only access to all aspects of Defender for Cloud Apps. Cannot change any  settings or take any actions. |

> [!NOTE]
> If you select **Manage admin access** from **Settings**, the above roles do not display.

A significant benefit in using Office 365 and Azure AD roles is that you can maintain your RBAC infrastructure in one place. You can assign and manages roles in Azure AD and have that be effective in Defender for Cloud Apps, too.

## Use Cloud App Security admin roles

Alternatively, you can use Defender for Cloud Apps roles. This enables you to separate the Azure AD and Office 365 roles from those in Defender for Cloud Apps.

> [!IMPORTANT]
> Only the Global Administrator or Security Administrator from Azure AD can assign other roles in the Defender for Cloud Apps portal.

These roles are described in the following table.

| Role                          | Description                                                  |
| ----------------------------- | ------------------------------------------------------------ |
| Global admin                  | Has full  access to Defender for Cloud Apps.                      |
| Security  reader              | Has read-only  access and can manage alerts.                 |
| Compliance  admin             | Has read-only  access, can manage alerts, and has limited control. |
| App/instance  admin           | Has full or  read-only permissions to all of the data in Defender for Cloud Apps that deals  exclusively with the specific app or instance of an app selected. |
| User group  admin             | Has full or  read-only permissions to all of the data in Defender for Cloud Apps that deals  exclusively with the specific groups assigned to them. |
| Cloud  Discovery global admin | Has  permission to view and edit all Cloud Discovery settings and data. |
| Cloud Discovery  report admin | Has  permissions to view all the data in Defender for Cloud Apps that deals exclusively  with the specific Cloud Discovery reports selected. |

> [!IMPORTANT]
> You can only assign user group admins permissions to imported Azure AD groups.

> [!NOTE]
> For a full list of administrative capabilities, review the following document: [Built-in Cloud App Security admin roles](/cloud-app-security/manage-admins?azure-portal=true#built-in-cloud-app-security-admin-roles).

### Override admin permissions

If you need to, you can override the permissions of an administrator's from Azure AD or Office 365. You do so by adding the user to Defender for Cloud Apps and then assigning the user account the required permissions.

For example, Adele is assigned the Security reader role in Azure AD. You decide that Adele needs to have Full access in Defender for Cloud Apps. You can add her manually to Defender for Cloud Apps and assign her Full access to override her role and allow her the necessary permissions in Defender for Cloud Apps.

### Add additional admins

To add additional admins, use the following procedure:

1. Navigate to the [Defender for Cloud Apps portal](https://portal.cloudappsecurity.com).
2. Sign in as a Global Admin in your Microsoft 365 tenant.
3. In the portal, select **Settings**. This is the cog next to your profile picture.
4. Select **Manage admin access**.
5. On the **Manage admin access** page, select the **+** symbol.
6. In the **Add admin access** dialog box, in the **Type admin UPN/email** text box, enter the user principal name or email address of the account you want to assign admin permissions to.
7. In the **Select the type of role for this admin** list, select the required admin role and then select **Add admin**.

:::image type="content" source="../media/add-admin.png" alt-text="A screenshot displays the Add admin dialog box. The administrator has entered the email address admin@contoso.com and is selecting the role from a drop-down list.":::

After you add a user with a role, that user is listed on the Manage admin access page.

### Add external admins

To add an external administrator, for example, from a Managed Security Service Provider (MSSP) as administrators of your Defender for Cloud Apps. To add external users, use the following high-level procedure:

1. Ensure that Defender for Cloud Apps is enabled on the source tenant
2. Obtain the appropriate external email address from your MSSP
3. Use the procedure outlined above to add the external admin using the email address you obtained from your MSSP

### Configuring admin roles and RBAC in Microsoft Defender for Cloud Apps

The following video demonstrates how to configure admin roles and manage RBAC in Defender for Cloud Apps:

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4MALF]
