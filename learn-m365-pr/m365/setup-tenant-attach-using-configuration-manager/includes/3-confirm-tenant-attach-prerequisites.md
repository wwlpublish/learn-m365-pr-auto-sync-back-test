Before you enable tenant attach, you must meet a set of prerequisites and enable a set of internet endpoints.

## Verify prerequisites

There are five main prerequisites to enable tenant attach:
- Create an Microsoft Intune tenant
- Verify the *Global Administrator* account
- Confirm your Azure public cloud environment
- Confirm user accounts are synced to Azure Active Directory from Active Directory
- Verify the remote provider for your tenant
- If you use a [central administration site](/mem/configmgr/core/plan-design/hierarchy/design-a-hierarchy-of-sites#BKMK_ChooseCAS) (CAS) for your Configuration Manager implementation and also have a remote provider, follow the instructions for the [CAS has a remote provider scenario](/mem/configmgr/core/servers/manage/cmpivot-changes#cas-has-a-remote-provider).

### Create a Microsoft Intune tenant

Microsoft Intune provides mobile device management (MDM) and mobile app management (MAM) from a secure cloud-based service that is administered using the Microsoft Endpoint Manager admin center. If you don't already have Intune set up, see [Try Microsoft Intune for free](/mem/intune/fundamentals/free-trial-sign-up) to quickly create an Intune tenant. When you complete the sign up process, you'll have a new tenant.

> [!TIP]
> For complete details about setting up Microsoft Intune, such as reviewing supported configurations, adding users, and assigning licenses, see [Set up Microsoft Intune](/learn/modules/set-up-microsoft-intune).

### Verify the global administrator account

The *Global Administrator* account must be supplied during the tenant attach configuration process. The *Global Administrator* is the person who signed up for the tenant. The *Global Administrator* has the permissions to do the following:
- Manage access to all administrative features for the tenant, as well as the related services that use Azure Active Directory.
- Assign administrator roles to others.
- Reset the password for any user and all other administrators.

To verify your tenant account permissions or determine your global administrator:
1. Sign in to the [Azure portal](https://portal.azure.com).
2. Find and select **Azure Active Directory**. <br>
   If necessary, click **More services** to located **Azure Active Directory**.
3. Click **Roles and administrators**. <br>
   You can verify your role.
4. If you aren't the global administrator, find and select **Global administrator** to help determine your global administrator.

For more information about roles, see [Azure AD roles](/azure/role-based-access-control/rbac-and-directory-admin-roles#azure-ad-roles).

### Confirm your Azure public cloud environment

To set up tenant attach, you must be using a standard Azure public cloud environment. If you set up Microsoft Intune following a standard process, such as following the free trial (mentioned above), you are using the Azure public cloud. If you set up your Azure tenant in a specific Azure cloud environment, such as the Azure China Cloud or an Azure US Government Cloud, you are using a non-public cloud.

> [!NOTE]
> Non-public cloud environments, such as Microsoft Azure China 21Vianet (Azure China Cloud) and Azure US Government Cloud, don't allow the **Upload to Microsoft Endpoint Manager admin center** option provided in Configuration Manager. This option is required for tenant attach and is described later in this module.

### Confirm user accounts are synced

For a user account to trigger device actions, the user account must be synced to Azure Active Directory from Active Directory (hybrid identity). To discover and sync your accounts, you can use either [Azure Active Directory user discovery](/mem/configmgr/core/servers/deploy/configure/about-discovery-methods#azureaddisc), or you can use [Active Directory user discovery](/mem/configmgr/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser).

> [!NOTE]
> If you are using Configuration Manager version 2010 or earlier, you must discover user accounts with both [Azure Active Directory user discovery](/mem/configmgr/core/servers/deploy/configure/about-discovery-methods#azureaddisc) and [Active Directory user discovery](/mem/configmgr/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser).
