To provide the best experience for your Azure Virtual Desktop users, use FSLogix profiles. FSLogix is designed to roam profiles in remote computing environments, such as Azure Virtual Desktop. User profiles are stored in per-user VHD or VHDX files.  At sign-in, this profile container is dynamically attached to the computing environment. The user profile is immediately available and appears in the system exactly like a native user profile.

## What is FSLogix?

FSLogix is a set of solutions that decouples the local user profile from a single Windows desktop and enables it to roam between multiple Windows machines.

A user profile contains data elements about an individual, including configuration information like desktop settings, persistent network connections, and application settings. A remote user profile provides a partition between user data and the operating system.

- With FSLogix solutions you can:
- Maintain user context in pooled desktop environments
- Minimize sign in times for pooled desktop environments
- Optimize file IO between session host and remote profile store

## Create FSLogix profile for Azure Virtual Desktop users

To use FSLogix to separate user profiles from the session host virtual machines (VM), we’ll need to configure Azure Storage and create an FSLogix profile share. These steps vary depending on the storage type and whether you’re using Azure Active Directory Domain Services (Azure AD DS) or Active Directory Domain Services (AD DS). The following steps cover how to configure Azure Files with Azure AD DS. The steps for AD DS are the same except for the “Enable Azure Active Directory authentication” section. The differences are called out in that section.

## Create the storage account

1. Sign in to the [Azure portal](https://ms.portal.azure.com/?azure-portal=truey#home).
1. Search for **Storage accounts** by using the Azure portal search box.
1. In the Storage Accounts command bar, select Create. The Create a storage account page appears.
1. Under *Project Details* select the **Subscription**, and then select or create a **Resource group** to contain your storage resources.
1. Under *Instance details*, enter a unique name for your Storage account.
1. Select the same Region as the AVD host pool.
1. For performance, select **Premium**.
1. For Premium Account type select File shares.
1. Leave **Redundancy** set to **Locally-redundant storage (LRS)**.
1. Select **Review + create** to validate your inputs, and then select **Create**.
1. Wait for the deployment to complete. This might take a minute.
1. Select **Go to resource**. The **Storage account** page displays details about your storage account.

## Enable Azure Active Directory authentication

The following steps cover how to enable authentication for Azure file shares with Azure AD DS. If you’re using AD DS, you need to register your Azure storage account with AD DS, and then set the required domain properties on the storage account. Use the AzFilesHybrid Azure PowerShell module on a device that is domain joined to your on-premises AD DS. The Join-AzStorageAccountForAuth cmdlet performs the equivalent of an offline domain join on behalf of the Azure storage account. For the step-by-step instructions to enable authentication with AD DS on-premises, see the related Docs article at the end of this module.

### Enable authentication for Azure file shares with Azure AD DS

1. In the Storage account menu, scroll to **Data Storage**, and then select **File shares**.
1. At the top of the page, look for **Active Directory** and select **Not configured**.
1. Under Azure Active Directory Domain Services, select **Set Up**.
1. Select **Enable Azure Active Directory Domain Services (Azure AD DS) for this file share**.
1. Select **Save**.
1. Select **Save** again.

## Assign roles to access storage data

### Assign role to Azure AD DC Administrators

You need to assign roles to the Azure AD DC Administrators group and to your Azure Virtual Desktop users.

1. Give the administrators the ability to modify NTFS permissions by assigning an elevated contributor role for the file share.
1. In the storage account you created, select **Access control (IAM)**.
1. Select **Add** > **Add role assignment**.
1. For **Role**, select **Storage File Data SMB Share Elevated Contributor** and click **Next**.
1. On the **Members** blade, ensure **Assign access to** is set to **User, group, or service principal**.
1. Click **Select Members**.
1. Click **AAD DC Administrators and click Select**.
1. Select **Review + assign**.
1. Select **Review + assign again**.

### Assign role to Azure Virtual Desktop users

1. Assign users a contributor role so they have permission to read and write file data in the SMB file share where the user profile virtual disks are stored.
1. In the storage account you created, select **Access control (IAM)**.
1. Select **Add > Add role assignment**.
1. For **Role**, select **Storage File Data SMB Share Contributor** and click **Next**.
1. On the **Members** blade, ensure **Assign access to** is set to **User, group, or service principal**.
1. Click **Select Members**.
1. Click **AAD DC Administrators and click Select**.
1. Select **Review + assign**.
1. Select **Review + assign again**.

## Enable FSLogix

Add a registry key to each VM registered to the host pool. You’ll need the storage account access key and the file share path.

1. From the start menu, run RegEdit as an administrator.
1. Go to *Computer_LOCAL_MACHINE*.
1. Create a key for the VMs called **Profiles**.
1. Create a registry key to store the SMB path you previously created. Under **Profiles**, add the following data type entries:

   |Type  |Name  |Data/Value|
   |----|---|--|
   |DWORD | Enabled | 1|
   |Multi-String Value | VHDLocations | File share location from Azure Files in SMB path format|

1. Create a registry key to Enable FSLogix. Under Profiles, add the following data type entries:

   |Type  |Name  |Data/Value|
   |----|---|--|
   |DWORD | Enabled | 1|

## Configure NTFS Permissions

### Get storage account access key

You'll need the storage account access key and file share path to configure NTFS permissions.

1. In your storage account, under **Security + networking**, select **Access keys**.

1. Select **show keys**.

1. Copy the value from one of the key fields to use it later.

### Get the file share path

1. In your storage account, in the left navigation, scroll down to **Data storage** and select **File shares**.
1. Select the file share you created.
1. Under **Settings**, select **Properties**.
1. Copy the URL.
1. Convert the URL from an HTTP path to an SMB path to use it later. For example, `https://myfslogixstorage.file.core.windows.net/profiles` converts to `\\myfslogixstorage.file.core.windows.net\profiles`.

### Login to a session host

1. Open an elevated command prompt on one of the session hosts.
1. Run the following commands where you replace placeholder values with the SMB file share path, the storage account access key, and the user’s Azure AD User Principal Name (UPN). The UPN would look something like kaicarter@contoso.onmicrosoft.com.

    ```cmd
    net use Z: [SMB path used in VHDLocations in the registry] /u:Azure\[storage account name] [storage access key]
    Icacls Z: /grant [user UPN]:(f)
    ```
